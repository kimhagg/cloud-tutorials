 # How to create a virtual machine instance and install nginx through google cloud

 This is a tutorial to help you set up your first cloud webserver via google cloud.

 ## Prerequisites
- Google cloud account
- Web browser

## Sections
1. [Creating a project](#creating-a-project)
2. [Project Setup](#project-setup)
3. [Create the virtual machine](#create-the-virtual-machine)

## Creating a project
1. Go to [console.cloud.google.com](https://console.cloud.google.com/) and click the button in the top-left on the right side of the Google cloud logo.

![Compute Engine](/Google%20Cloud/Assets/Create%20a%20new%20project_1.jpg)

2. In the smaller window that pops up click the "NEW PROJECT" text that appears in the top-right.
![Compute Engine](/Google%20Cloud/Assets/Create%20a%20new%20project.jpg)

3. Give your project a name and select the organization (if applicable) that should handle the project. Then click "CREATE".
![Compute Engine](/Google%20Cloud/Assets/Name%20your%20project.jpg)

## Project setup
1. Click the hambuger menu ![Hamburger Icon](https://upload.wikimedia.org/wikipedia/commons/b/b2/Hamburger_icon.svg)
 in the top-left to the left of the Google cloud logo.


2. Click compute engine.
![Compute Engine](/Google%20Cloud/Assets/Compute_Engine.jpg)


3. Click enable compute engine API.
![Compute Engine](/Google%20Cloud/Assets/Enable%20Compute%20Engine.jpg)

4. Wait until button says manage, then re-do step 1 and 2. If it takes you past the enable page, instead continue to step 5.
![Compute Engine](/Google%20Cloud/Assets/Manage%20API.jpg)

5. Click the console icon in the top-right.
![Compute Engine](/Google%20Cloud/Assets/Console_Icon.jpg)

6. The console will open at the bottom of the page.
![Compute Engine](/Google%20Cloud/Assets/Console%20%20opens%20at%20the%20bottom.png)


7. Type gcloud init. A small windows will appears asking for your permision for the console shell have access to google cloud CLI. Press authorize.
![Compute Engine](/Google%20Cloud/Assets/Authorize_Cloud_Shell.jpg)


8. Press ``1``, then ``Enter``, then ``1``, then ``Enter`` again. This selects to re-initialize the project and it selects your primary email to use with the project.

9. When asked for what project to use, find project name (in yellow) and then enter the numeric option for that project name.
![Compute Engine](/Google%20Cloud/Assets/Project%20name.jpg)


10. Press enter to select default zone, a list of zones will come up. Type ```europe-north1-a``` and press enter to set it as default zone. If you want a different zone you can look through the list, if the zone you want isn't in the first 50, type ```list``` to show all zones.

11. Copy below code using the copy button or CTRL+C, then paste into the terminal using CTRL+SHIFT+V. This will add a rule to the firewall that says "if an instance has the tag http-server then open port 80 for it".
```bash
gcloud compute firewall-rules create default-allow-http \
    --direction=INGRESS \
    --priority=1000 \
    --network=default \
    --action=ALLOW \
    --rules=tcp:80 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=http-server
```

## Create the virtual machine
1. If the console is not open. Click the console icon in the top-right.
![Compute Engine](/Google%20Cloud/Assets/Console_Icon.jpg)

2. Copy below code using CTRL+C then paste into the terminal using CTRL+SHIFT+V.
```bash
echo "Please enter instance name [-a-z0-9]:"
read instance_name

gcloud compute instances create $instance_name \
    --machine-type=e2-medium \
    --tags=http-server \
    --metadata=startup-script='#!/bin/bash
apt-get update -y
apt-get install nginx -y'
```
3. Type a name in lowercase letters, numbers and use - for spaces. Then press Enter.

4. Wait about a minute for the command to complete. After the command completes the server should start about a minute or two later.

Congratulations it's finished! You just need to click on the external ip to show the website.
![External IP](/Google%20Cloud/Assets/External%20IP.jpg)
