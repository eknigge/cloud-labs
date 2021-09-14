# Azure VM With Ubuntu and NGINX Web Server &middot;

> Hands-on Lab

|                     |                       |
| :------------------ | :-------------------- |
| *Cloud Vendor*      | **Microsoft Azure**   |
| *Proficiency Level* | **Cloud  Enthusiast** |
| *Tags*              | ![https://img.shields.io/badge/%20-Linux-blue](https://img.shields.io/badge/%20-Linux-blue) ![https://img.shields.io/badge/%20-NGINX-blue](https://img.shields.io/badge/%20-NGINX-blue) ![https://img.shields.io/badge/%20-Ubuntu-blue](https://img.shields.io/badge/%20-Ubuntu-blue) ![https://img.shields.io/badge/%20-Virtual%20Machine-blue](https://img.shields.io/badge/%20-Virtual%20Machine-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue) |

## Lab Scenario
In this lab, you will provision a Microsoft Azure Virtual Machine (VM) that runs Ubuntu Linux server operating system. Once the VM is provisioned, you will install a NGINX Web server software on it. After the Web server is installed, you will verify that it is running by accessing its home page with a browser. Last, you will modify the home page to show the text `Hello, computelabadmin!`.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Provision a Linux VM in Microsoft Azure
- Connect to the newly provisioned VM using an SSH client
- Use the command line to manually install a Web server on the VM
- Connect to the Web server using a browser
- Modify the Web server’s home page
- Stop the VM

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection
- A work, school or personal Microsoft Account used to access Microsoft Azure Management Portal
- A subscription for Microsoft Azure

## Exercises

### Exercise #1: Provision a Linux VM in Microsoft Azure

In this exercise, you will provision a Linux virtual machine (VM) running Ubuntu Server distribution in Microsoft Azure.

1. Sign into the Microsoft Azure Management Portal at [http://portal.azure.com](http://portal.azure.com) using your Microsoft Account.
2. Click on ![Create a resource](media/azure-create-a-resource.png) in the upper left corner right under the Microsoft Azure logo.
3. In the search box search for *Ubuntu Server 20.04*.
4. Select *Ubuntu Server 20.04 LTS by Canonical* from the list of results.
5. Click on the ![Create button](media/azure-create-button.png) button.
6. On the *Basics* tab in section, *Project Details* fill in the following information:
  - *Subscription* → `[select your Microsoft Azure subscription]`
  - *Resource group* → Click on  `Create new`
  - *Resource group name* (the text field in the pop up) → `azvmnginxlab-[initials]-rg`, where `[initials]` are your first, middle, and last name initials
7. On the *Basics* tab in section, *Instance Details* fill in the following information:
  - *Virtual machine name* → `azvmnginxlab-[initials]-vm01`
  - *Region* → `West US 2`
  - *Availability options* → `No infrastructure redundancy required`
  - *Image* → `Ubuntu Server 20.04 LTS - Gen1`
  - *Size* → Click on `See all sizes`, select `B1s` then click on the ![Select button](media/azure-select-button.png) button.

  > If the VM size is not available for selection, try changing the region to `West US`.
8. On the *Basics* tab in section, *Administrator Account* fill in the following information:
  - *Authentication type* → `Password`
  - *Username* → `computelabadmin`
  - *Password* → `[type a strong password]`
  - *Confirm password* → `[type the same password as above]`
9. On the *Basics* tab in section, *Inbound port rules* fill in the following information:
  - *Public inbound ports* → `Allow selected ports`
  - *Selected inbound ports* → Select `HTTP (80)` and `SSH (22)`
10. Click on ![Next : Disks button](media/azure-next-disks-button.png) button.
11. On the *Disks* tab, leave the default selections.
12. Click on ![Next : Networking button](media/azure-next-networking-button.png) button.
13. On the *Networking* tab, leave the default selections.
14. Click on ![Next : Management button](media/azure-next-management-button.png) button.
15. On the *Management* tab, leave the default selections.
16. Click on the ![Next : Advanced button](media/azure-next-advanced-button.png) button.
17. On the *Advanced* tab, leave the default selections.
18. Click on the ![Next : Tags button](media/azure-next-tags-button.png) button.
19. On the *Tags* tab, add the following tags:
  - *Role* → `web`
  - *Lab* → `azvmnginxlab`
  - *Owner* → `[your full name]`
  - *OwnerEmail* → `[your email address]`
20. Click on the ![Next : Review + create button](media/azure-next-review-and-create-button.png) button.
21. Review the summary and click on the ![Create button](media/azure-create-button.png) button.
    
    > You may need to provide some additional information on this screen. Use your best judgement for the required information.
22. Wait until the deployment is complete.
23. Once the deployment is complete, click on the ![Resource groups button](media/azure-resource-groups-button.png) button in the left-hand menu list under the Microsoft Azure logo.
24. Find the `azvmnginxlab-[initials]-rg` resource group in the list and click on it.
25. Verify the following resource types exist:
  - `Virtual network`
  - `Virtual machine`
  - `Public IP address`
  - `Network security group`
  - `Disk`
  - `Network interface`

#### Exercise Summary
At this point, you have learned how to provision an Ubuntu Linux virtual machine (VM) in the Microsoft Azure cloud. Note that although you requested the creation of a single resource, multiple were created. 

### Exercise #2: Connect to the newly provisioned VM using an SSH client

In this exercise, you will connect to the newly provisioned VM using an SSH client.

> You need to have an SSH client installed on your machine. On MacOS, Windows 10, or Linux the SSH client is available by default. For older Windows versions, you will need to download third-party SSH client software.

1. Click on the `azvmnginxlab-[initials]-vm01` virtual machine resource.
2. From the *Overview* blade note the *Public IP address* of the virtual machine.
3. Open the terminal on your local machine.
4. Connect to the virtual machine via SSH by typing the following at the command prompt:
   ```
   $ ssh computelabadmin@<the_ip_address_from_step_2>
   ```
5. Confirm the key message.
6. Type the password for the virtual machine at the prompt.

#### Exercise Summary

At this point, you have learned how to connect to the remote Virtual Machine using an SSH client

### Exercise #3: Use the command line to manually install the NGINX web server on the VM

In this exercise, you will use the command line to update the Ubuntu repositories and install the NGINX web server on the VM.

1. While connected to the VM, update the Ubuntu repositories by typing the following at the command prompt:
   ```
   $ sudo apt-get update
   ```
   > If asked, you have to type the computelabadmin’s password because you use the sudo command.
2. Once the update is complete, install the NGINX web server by typing the following at the command prompt:
   ```
   $ sudo apt-get install nginx
   ```
3. Respond with `Y` (yes) to the prompts on the screen.
4. Once the installation completes, start the NGINX web server using the following command:
   ```
   $ sudo /etc/init.d/nginx start
   ```

#### Exercise summary

At this point, you have learned how to install and start an NGINX web server on the VM.

### Exercise #4: Connect to the Web server using a browser

In this exercise, you will use a browser to connect to the Web server and load its home page.

1. Open a browser on your local machine.
2. In the address bar, type the *Public IP address* from *Step 2* in *Exercise #2* above.
3. You should see the home page served by the NGINX web server.

#### Exercise Summary

At this point, you have learned how to install and run an NGINX Web server on the remote Virtual Machine. You have also verified that you can access the web server’s home page from your local machine using a browser.

### Exercise #5: Modify the Web server’s home page

In this exercise, you will modify the NGINX web server’s home page to show a custom message.

1. While connected via SSH to the VM, open the HTML file that describes the NGINX home page in Vi by typing the following at the prompt:
   ```
   sudo vi /var/www/html/index.nginx-debian.html
   ```
2. Using the arrows on the keyboard, position the cursor after the exclamation mark on the line that has the following: 
   ```
   <h1>Welcome to nginx!</h1>
   ```
3. Press the `i` key on the keyboard to enter *INSERT* mode in Vi editor.
4. Type the following:
   ```
   Hello, <code>computelabadmin</code>!
   ```
5. Press the `ESC` key on the keyboard to exit *INSERT* mode in Vi.
6. Type the following to save the file and exit Vi
   ```
   :wq
   ```
7. Switch to your browser window and reload the page. You should see the updated home page.

#### Exercise Summary

At this point, you have learned how to locate the NGINX web server’s home page (also called index page) source and modify it as well as verify that the changes are visible using your local machine’s browser.

### Exercise #6: Stop the VM

In this exercise, you will learn how to stop the VM to avoid additional charges while not using it.

1. Sign into the Microsoft Azure Management Portal at http://portal.azure.com using your Microsoft Account.
2. Click on the ![Resource groups button](media/azure-resource-groups-button.png) button in the left-hand menu list under the Microsoft Azure logo.
3. Find the `azvmnginxlab-[initials]-rg` resource group in the list.
4. In the *Overview* blade, find the `azvmnginxlab-[initials]-vm01` virtual machine resource and click on it.
5. Click on the ![Stop button](media/azure-stop-button.png) on top of the *Overview* blade.
6. When prompted, click on the ![OK button](media/azure-ok-button.png)

#### Exercise Summary

At this point, you have learned how to stop the VM and save on cost when you are not using it.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)