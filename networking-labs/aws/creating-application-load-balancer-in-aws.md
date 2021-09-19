# Creating an Application Load Balancer in AWS

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-EC2-blue](https://img.shields.io/badge/%20-EC2-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue) |

## Lab Scenario
In this lab, you will provision an Applicaiton Load Balancer in AWS. You will configure the Load Balancer to balance web traffic between two web servers deployed on Amazon EC2 instances.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Provision an Application Load Balancer in AWS.
- Configure the Application Load Balancer to balance web traffic between EC2 instances.

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection.
- An AWS Account used to access AWS Management Console.
- You will need to create two EC2 instances following the [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md). You must follow the steps described in that lab to create and configure the two instances. However some modifications for each instance will be required. Those will be described in the exercises below. 

## Lab Instructions

### Exercise #1: Provision the First EC2 Instance

In this exercise you will provision the first EC2 instance that will be connected to the load balancer. Follow the instructions in the [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) with the following modifications:

1. In *step 10* of *exercise #1*, change the *Name* tag as follows:
   - *Name* → `[initials]-awsnetworkinglab-instance01`, where `[initials]` are your first, middle, and last name initials
2. In *step 12* of *exercise #1*, change the *Security group name* and *Security group description* as follows:
  - *Security group name* → `[initials]-awsnetworkinglab-sg`, where `[initials]` are your first, middle, and last name initials
  - *Security group description* → `[your_full_name]'s security group for my first networking compute lab on AWS`
3. In *step 17* of *exercise #1*, change the *Key pair name* as follows:
  - *Key pair name* → `[initials]-awsnetworkinglab-ec2-keypair`, where `[initials]` are your first, middle, and last name initials

### Exercise #2: Install NGINX Web Server on the First EC2 Instance and Modify its Home Page

In this exercise you will connect the first EC2 instance, install the NGINX web server and modify its home page. Follow the instructions in the [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) with the following modifications:

1. Follow *exercise #2* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to connect to the first EC2 instance.
2. Follow *exercise #3* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to install the NGINX web server.
3. Follow *exercise #5* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to modify the web server's home page.
4. In *step 4* of *exercise #5* use the following HTML code:
   ```
   Hello, <code>I am EC2 Instance #1</code>!
   ```

### Exercise #3: Provision the Second EC2 Instance

In this exercise you will provision the second EC2 instance that will be connected to the load balancer. Follow the instructions in the [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) with the following modifications:

1. In *step 10* of *exercise #1*, change the *Name* tag as follows:
   - *Name* → `[initials]-awsnetworkinglab-instance02`, where `[initials]` are your first, middle, and last name initials
2. In *step 12* of *exercise #1*, change the radio button to `Select an existing security group`.
3. Select the security group with *Security group name* `[initials]-awsnetworkinglab-sg`, where `[initials]` are your first, middle, and last name initials.
3. In *step 17* of *exercise #1*, select the existing key pair with *Key pair name* → `[initials]-awsnetworkinglab-ec2-keypair`, where `[initials]` are your first, middle, and last name initials.

### Exercise #4: Install NGINX Web Server on the First EC2 Instance and Modify its Home Page

In this exercise you will connect the second EC2 instance, install the NGINX web server and modify its home page. Follow the instructions in the [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) with the following modifications:

1. Follow *exercise #2* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to connect to the first EC2 instance.
2. Follow *exercise #3* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to install the NGINX web server.
3. Follow *exercise #5* from [AWS EC2 Instance With Ubuntu and NGINX Web Server lab](../../compute-labs/aws/aws-ec2-with-ubuntu-and-nginx-web-server.md) to modify the web server's home page.
4. In *step 4* of *exercise #5* use the following HTML code:
   ```
   Hello, <code>I am EC2 Instance #2</code>!
   ```

### Exercise #5: Provision an Application Load Balancer in AWS

In this exercise, you will provision an Application Load Balancer in AWS.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. On the new page, scroll down the left-hand navigation and find section *Load Balancing*.
5. Click on the *Load Balancers*.
6. Click on the ![Create Load Balancer button](media/aws-create-load-balancer-blue-button.png) button.
7. Click on the ![Create button](media/aws-create-blue-button.png) button under *Application Load Balancer (HTTP/HTTPS)*.
8. In *Step 1: Configure Load Balancer*, in the *Basic Configuration* section, fill in the following information:
  - *Name* → `[initials]-networkinglab-ec2-lb`
  - *Scheme* → `internet-facing`
  - *IP address type* → `ipv4`
9. In *Step 1: Configure Load Balancer*, the *Availability Zones* section, select the following:
  - `us-west-2a`
  - `us-west-2b`
  - `us-west-2c`
  - `us-west-2d`
10. In *Step 1: Configure Load Balancer*, expand the *Tags* section, and add the following tags:
  - *Name* → `[initials]-networkinglab-ec2-lb`
  - *Role* → `web`
  - *Lab* → `networkinglab`
  - *Owner* → `[your name]`
  - *OwnerEmail* → `[your email]`
11. Click on the ![Next: Configure Security Settings button](media/aws-next-configure-security-settings-button.png) button.
12. Click on the ![Next: Configure Security Groups button](media/aws-next-configure-security-groups-button.png) button.
13. In *Step 3: Configure Security Groups*, change the radio button to `Create a new security group` and use the following values:
  - *Security group name* → `[initials]-awsnetworkinglab-lb-sg`, where `[initials]` are your first, middle, and last name initials
  - *Security group description* → `[your_full_name]'s security group for my load balancer on AWS`
14. Click on the ![Next: Configure Routing button](media/aws-next-configure-routing-button.png) button.
15. In *Step 4: Configure Routing*, in the *Target group* section, fill in the following:
  - *Target group* → `New target group`
  - *Name* → `[initials]-awsnetlab-web-instances`, where `[initials]` are your first, middle, and last name initials
16. Leave the rest of the selections as by default.
17. Click on the ![Next: Register Targets button](media/aws-next-register-targets-button.png) button.
18. In *Step 5: Register Targets*, in the *Instances* section, select the following instances:
  - `[initials]-awsnetworkinglab-instance01`
  - `[initials]-awsnetworkinglab-instance02`
  
    where `[initials]` are your first, middle, and last name initials
19. Click on the ![Add to registered button](media/aws-add-to-registered-blue-button.png) button.
20. Click on the ![Next: Review button](media/aws-next-review-button.png) button.
21. Click on the ![Create button](media/aws-create-button.png) button.
22. Once the Application Load Balancer is deployed, click on the ![Close button](media/aws-close-button.png) button

#### Exercise Summary
At this point, you have learned how to provision an Application Load Balancer in AWS.

### Exercise #6: Testing an Application Load Balancer in AWS

In this exercise, you will test the Application Load Balancer that you created in AWS. You can test the Application Load Balancer by accessing its DNS name from a browser.

1. Click on the `[initials]-networkinglab-ec2-lb` Application Load Balancer in the list.
2. From the *Description* tab, copy the *DNS name*.
3. Open a new browser window, paste the above DNS name in the address bar and press *Enter*.
4. The page shows the home page of the NGINX server on `[initials]-awsnetworkinglab-instance01`.
5. Refresh the page in the browser.
6. The page shows the home page of the NGINX server on `[initials]-awsnetworkinglab-instance02`.

> Depending on your browser’s caching settings, you may need to refresh the page more than once to see the second home page

#### Exercise Summary

In this exercise you learned how to test the load balancer that you deployed in AWS.

### Exercise #7: Stop and Terminate the Resources

In this exercise you will delete the resources to save on cost.

### Exercise #6: Stop the EC2 Instance

In this exercise, you will learn how to stop and terminate the resources and not incur any additional charges for them.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. Click on the *Instance ID* next to the `[initials]-awsnetworkinglab-instance01` EC2 instance from the list, where `[initials]` are your first, middle, and last name initials.
5. From the ![Instance State button](media/aws-instance-state-dropdown-button.png), select the *Terminate instance* option.
6. Click on the ![Terminate button](media/aws-terminate-orange-button.png) on the *Terminate instances* pop-up to confirm.
7. Repear steps 4 through 6 for the `[initials]-awsnetworkinglab-instance02` EC2 instance.
8. Scroll down the left-hand navigation and find section *Load Balancing*.
9. Click on the *Load Balancers*.
10. Select the `[initials]-networkinglab-ec2-lb` load balancer.
11. Click on the ![Actions button](media/aws-actions-dropdown-button.png) button and select *Delete*.
12. Confirm the deletion by clickin on the ![Yes, Delete button](media/aws-yes-delete-blue-button.png) button.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)