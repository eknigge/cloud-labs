# Restricting Access To Target Group EC2 Instances Behind AWS Application Load Balancer Using Security Groups

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) ![https://img.shields.io/badge/%20-EC2-blue](https://img.shields.io/badge/%20-EC2-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Security%20Groups-blue](https://img.shields.io/badge/%20-Security%20Groups-blue) ![https://img.shields.io/badge/%20-Web%Server-blue](https://img.shields.io/badge/%20-Web%Server-blue) |

## Lab Scenario

In this lab, you will configure Security Groups (SG) in Amazon AWS to protect the Target Group EC2 instances from direct HTTP access. Also, you will restrict the SSH access to the Target Group EC instances to your IP address, thus preventing anybody else accessing the EC2 instances via SSH.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Configure the security group to accept HTTP traffic from the Application Load Balancer only.
- Configure the security group to accept SSH traffic from your IP address only.
- Test the security group configuration.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- A free AWS Account used to access the AWS Management Console.
- You will need to complete the AWS Application Load Balancer HTTPS configuration by following the instructions from [Configuring HTTPS On AWS Application Load Balancer](configuring-https-on-aws-application-load-balancer.md).

## Lab Instructions

### Exercise 1: Determine the Public IP Address Used by Your Local Network

Here is how you can determine the public IP address used by your local network. This IP address cannot be used to access your local machine from the Internet, but it is the appears as originating IP addres for requests that you make to services and web sites:

1. Go to [https://www.google.com](https://www.google.com).
2. Type `what is my ip address` in the search box.
3. Google will return the public IP address your local machine will use for requests to external services and web sites. Note this IP address; you will need it for the exercises.

#### Exercise Summary

At this point you have learned how to determine the public IP address for your local machine.

### Exercise 2: Determine the Public IP Addresses of the Target Group EC2 Instances

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. On the new page, scroll down the left-hand navigation and find section *Load Balancing*.
5. Click on the *Load Balancers*.
6. Find the `[initials]-networkinglab-ec2-lb` load balancer, and click on it.
7. On the *Listeners* tab for the load balancer, click on the *target group* under *Rules* column for one of the listeners.
8. On the *Target groups* page, click on the `[initials]-networkinglab-web-instances` target group.
9. Click on the first instance from the *Registered targets* list.
10. Select the `[initials]-awsnetworkinglab-instance01` instance.
11. From the *Details* tab, copy the `Public IPv4 address` for the instance. Note this IP address; you will need it for the exercises.
12. Follow the steps above to note the `Public IPv4 address` for the `[initials]-awsnetworkinglab-instance02` instance

#### Exercise Summary

At this point you have learned how to find the public IP addresss for the EC2 instances used as *target group* for the Application Load Balancer.

### Exercise 3: Modify the Security Group for the EC2 Instances in the Target Group

In this exercise you will modify the rules for the security group used by the EC2 instances to restrict the traffic.

1. Scroll down the left-hand navigation and find section *Network & Security*.
2. Click on the *Security Groups*.
3. Find the `[initials]-awsnetworkinglab-sg` security group and click on the ID next to the name.
4.  Click on the [Edit inbound rules button](media/aws-edit-inbound-rules-button.png).
5.  Remove the `0.0.0.0/0` source IP range for all rules.
6.  For the `SSH` rule, add the IP address for your local network that you obtained in *exercise #1*.
7.  For the `HTTPS` rule, select the `[initials]-awsnetworkinglab-lb-sg` security group.
8.  Delete the `HTTP` rule.

#### Exercise Summary

At this point you learned how to restrict the access to the EC2 instances to allow only your local machine's address for SSH and only the Application Load Balancer for web traffic.

### Exercise 3: Test the Connectivity

In this exercise you will verify the configuration is working as expected.

1. Scroll down the left-hand navigation and find section *Load Balancing*.
2. Click on the *Load Balancers*.
3. Find the `[initials]-networkinglab-ec2-lb` load balancer, and click on it.
4. From the *Description* tab copy the `DNS name` for the load balancer.
5. Open a new browser window and type `https://` in the address line, paste the *DNS name* after that, and press *Enter*.
6. You will see a browser warning. Add the URL to your browser's exception list and load the page.
7. Paste the IP address of the first EC2 instance in the address line and press *Enter*. You obtained this IP address in *exercise #2*.
8. Verify that the page doesn't load.
9. Paste the IP address of the second EC2 instance in the address line and press *Enter*. You obtained this IP address in *exercise #2*.
10. Verify that the page doesn't load.
11. Use an SSH client to connect and sign into the first EC2 instance from your local machine.
12. Verify that you can connect ans sign into the first EC2 instance.
13. Use an SSH client to connect and sign into the second EC2 instance from your local machine.
14. Verify that you can connect ans sign into the second EC2 instance.
15. Ask a colleague of yours to SSH and sign into one or both EC2 instances using your credentials.  It may be helpful to set a connection timeout value. To do that add the following flag to the ssh connection command `-o ConnectTimeout=[time]` where `[time]` is the timeout time in seconds.
16. Verify that your colleague is not able to connect and sign in to any of the above EC2 instances.

#### Exercise Summary

At this point you verified that the configuration works as expected and the infrastructure is secured.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)