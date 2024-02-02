 # How to create a virtual machine instance and install nginx through google cloud

 This is a tutorial to help you set up your first cloud webserver via google cloud.

 ## Prerequisites
- Google cloud account
- Web browser

## Creating a project
1. Go to [console.cloud.google.com](https://console.cloud.google.com/) and click the button in the top-left on the right of the Google cloud logo.
2. In the smaller window that pops up click the "NEW PROJECT" text that appears in the top-right.
3. Give your project a name and select the organization (if applicable) that should handle the project. Then click "CREATE"

## Project setup
1. Click the hambuger menu ![Hamburger Icon](https://upload.wikimedia.org/wikipedia/commons/b/b2/Hamburger_icon.svg)
 in the top-left to the left of the Google cloud logo


2. Click compute engine
![Compute Engine](/Assets/Compute_Engine.jpg)


3. Click enable compute engine API
![Compute Engine](/Assets/Enable%20Compute%20Engine.jpg)

5. Wait until button sais manage, then re-do previous two steps. If it takes you past the enable page, instead continue to step 6.

6. Click the console icon in the top-right. It's a square with the text >_ inside it.
![Compute Engine](/Assets/Console%20Icon.jpg)

7. The console will open at the bottom of the page.
![Compute Engine](/Assets/Console%20%20opens%20at%20the%20bottom.png)


8. Type gcloud init. A small windows will appears asking for your permision for the console shell have access to google cloud CLI. Press authorize
![Compute Engine](/Assets/Authorize_Cloud_Shell.jpg)


9. Press ``1``, then ``Enter``, then ``1``, then ``Enter`` again. 

10. When asked for what project to use, find project name and then enter the numeric option for that project name.
![Compute Engine](/Assets/Project%20name.jpg)


11. Press enter to select default zone, a list of zones will come up. Type ```europe-north1-a``` and press enter to set it as default zone. If you want a different zone you can look through the list, if the zone you want isn't in the first 50, type ```list``` to show all zones.

## Create the virtual machine
1. If the console is not open. Click the console icon in the top-right. It's a square with the text >_ inside it.
![Compute Engine](/Assets/Console%20Icon.jpg)

2. Copy below code using CTRL+C then paste into the terminal using CTRL+SHIFT+V
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

4. Wait about 5 minutes for the command to complete. After the command completes the server should start about a minute or two later.

Congratulations it's finished!
