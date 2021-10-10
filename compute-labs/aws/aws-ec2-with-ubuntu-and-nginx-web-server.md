# AWS EC2 Instance With Ubuntu and NGINX Web Server

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**   |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Linux-blue](https://img.shields.io/badge/%20-Linux-blue) ![https://img.shields.io/badge/%20-NGINX-blue](https://img.shields.io/badge/%20-NGINX-blue) ![https://img.shields.io/badge/%20-Ubuntu-blue](https://img.shields.io/badge/%20-Ubuntu-blue) ![https://img.shields.io/badge/%20-Virtual%20Machine-blue](https://img.shields.io/badge/%20-Virtual%20Machine-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue) |

## Lab Scenario
In this lab, you will provision an AWS EC2 Instance (VM) that runs Ubuntu Linux server operating system. Once the instance is provisioned, you will install a NGINX Web server software on it. Once the Web server is installed, we will verify that it is running by accessing its home page with a browser. Last, we will modify the home page to show the text `Hello, computelabadmin!`.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Provision an EC2 instance in AWS.
- Connect to the newly provisioned instance using an SSH client.
- Use the command line to manually install a Web server on the instance.
- Connect to the Web server using a browser.
- Modify the Web server’s home page.
- Stop the instance.

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection.
- An AWS Account used to access AWS Management Console.

## Exercises

### Exercise #1: Provision an EC2 Instance with Ubuntu Linux
In this exercise, you will provision an EC2 instance that runs Ubuntu Linux operating system.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials. Verify that the correct region is selected, if it is not you will not be able to create an *EC2* instance. 
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. On the new page, click on the ![Launch instance button](media/aws-launch-instance-button.png) and select *Launch instance*.
5. On the *Choose an Amazon Machine Image (AMI)* screen, find the *Ubuntu Server 20.04 LTS (HVM), SSD Volume Type (Free tier eligible)* AMI in the list.
6. Select the image by clicking the ![Select button](media/aws-select-blue-button.png) button.
7. On the *Choose an Instance Type* screen, select *t2.micro (Free tier eligible)* instance type and click on the ![Next: Configure Instance Details button](media/aws-next-configure-instance-details-button.png) button.
8. On the next screen, *Configure Instance Details*, leave everything by default and click on the ![Next: Add Storage button](media/aws-next-add-storage-button.png) button.
9. On the *Add Storage* screen, leave the values as default and click on the ![Next: Add Tags button](media/aws-next-add-tags-button.png) button.
10. On the next screen, *Add Tags*, use the ![Add tag button](media/aws-add-tag-button.png) and ![Add another tag button](media/aws-add-another-tag-button.png) buttons to add the following tags:
  - *Name* → `[initials]-awsec2nginxweblab-instance`, where `[initials]` are your first, middle, and last name initials
  - *Role* → `web`
  - *Lab* → `awsec2nginxweb`
  - *Owner* → `[your full name]`
  - *OwnerEmail* → `[your email address]`
11. Click on the ![Next: Configure Security Group button](media/aws-next-configure-security-group-button.png) button to go to the next step.
12. On the *Configure Security Group* screen, change the following:
  - *Security group name* → `[initials]-awsec2nginxweblab-sg`, where `[initials]` are your first, middle, and last name initials
  - *Security group description* → `[your_full_name]security group for my first EC2 compute lab on AWS`
13. Click on the ![Add Rule button](media/aws-add-rule-button.png) button to add new security rule.
14. Click on the drop down `Custom TCP` and select `HTTP` from the list.
15. Click on the ![Review and Launch button](media/aws-review-and-launch-blue-button.png) button to review the information for your EC2 instance.
16. Review the information for the EC2 instance and click on the ![Launch button](media/aws-launch-blue-button.png) button.
17. In the pop-up window, change the selection to:
  - `Create a new key pair`
  - *Key pair type* → `RSA`
  - *Key pair name* → `[initials]-awsec2nginxweblab-ec2-keypair`, where `[initials]` are your first, middle, and last name initials
18. Click on the ![Download Key Pair button](media/aws-download-key-pair-button.png) button and save the key file on your local machine.
  > **Important:** Save the key file in a secure location on your local machine. If you lose the key file, you will not be able to connect to the instance remotely.
19. Click on the ![Launch Instances button](media/aws-launch-instances-blue-button.png) to launch the instance.
20. On the confirmation screen, click on the ![View Instances button](media/aws-view-instances-blue-button.png) button to see the list of all instances.
21. Find your instance in the list and confirm it is in a `Running` state.

#### Exercise Summary

At this point, you have learned how to provision an Ubuntu Linux EC2 instance in AWS.

### Exercise #2: Connect to the newly provisioned VM using an SSH client

In this exercise, you will connect to the newly provisioned EC2 instance using an SSH client.

> You need to have an SSH client installed on your machine. On MacOS, Windows 10, or Linux the SSH client is available by default. For older Windows versions, you will need to download third-party SSH client software.

1. Click on the *Instance ID* next to the `[initials]-awsec2nginxweblab-instance` EC2 instance from the list, where `[initials]` are your first, middle, and last name initials.
2. On the *Instance summary* screen, note the *Public IPv4 address* of the instance.
3. On your local machine, open a terminal and change to the folder where you saved the key file.
4. If you are using Mac OS or Linux, change the access mode for the key file byt typing:
   ```
   chmod 400 [initials]-awsec2nginxweblab-ec2-keypair.pem
   ```
   where `[initials]` are your first, middle, and last name initials
5. Connect to the EC2 instance via SSH by typing the following at the SSH command prompt:
   ```
   $ ssh -i ./[initials]-awsec2nginxweblab-ec2-keypair.pem ubuntu@[the_ip_address_from_step_2]
   ```
   where `[initials]` are your first, middle, and last name initials

#### Exercise Summary
At this point, you have learned how to connect to the remote EC2 instance using an SSH client.

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

### Exercise #6: Terminate the EC2 Instance

In this exercise, you will learn how to stop the EC2 instance and not incur any additional charges for it.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. Click on the *Instance ID* next to the `[initials]-awsec2nginxweblab-instance` EC2 instance from the list, where `[initials]` are your first, middle, and last name initials.
5. From the ![Instance State button](media/aws-instance-state-dropdown-button.png), select the *Stop instance* option.
6. Click on the ![Terminate button](media/aws-terminate-orange-button.png) on the *Terminate instances* pop-up to confirm.

#### Exercise Summary
At this point, you have learned how to stop the EC2 instance and save costs when you are not using it.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)