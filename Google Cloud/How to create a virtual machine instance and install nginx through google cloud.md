 # How to create a virtual machine instance and install nginx through google cloud

 This is a tutorial to help you set up your first cloud webserver via google cloud.

 ## Prerequisites
- Google cloud account
- Web browser

## Creating a project
1. Go to [console.cloud.google.com](https://console.cloud.google.com/) and click the button in the top-left on the right of the Google cloud logo .
2. In the smaller window that pops up click the "NEW PROJECT" text that appears in the top-right.
3. Give your project a name and select the organization (if applicable) that should handle the project. Then click "CREATE"

## Project setup
1. Click the hambuger menu ![Hamburger Icon](https://upload.wikimedia.org/wikipedia/commons/b/b2/Hamburger_icon.svg)
 in the top-left to the left of the Google cloud logo

--click compute engine
 
--click enable compute engine API

--wait until button said manage, then re-do previous two steps

--click the console icon in the top-right. It's a square with the text >_ inside it.

--type gcloud init

--press authorize

--press 1, then enter, then 1, then enter

--when asked for what project to use, find project name and then enter the numeric option for that project name.

--instruction for how to find project name

--press enter to select default zone, a list of zones will come up, if the zone you want isn't there, type ```list``` to show all zones.

--add ```europe-north1-a``` as default zone either by typing the name or typing the list entry number

## Create the virtual machine
--if the console is not open. click the console icon in the top-right. It's a square with the text >_ inside it.

1. Copy below code into the terminal
```bash
echo "Please enter instance name [-a-z0-9]:"
read instance_name

gcloud compute instances create $instance_name \
    --machine-type=e2-medium \
    --tags=http-server \
    --metadata=startup-script='#!/bin/bash
apt-get update -y
apt-get install nginx -y'\
```
2. Type a name in lowercase letters, numbers and use - for spaces. Then press Enter.

3. Wait for the command to complete.

Congratulations it's finished!