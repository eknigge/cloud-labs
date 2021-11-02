# Configuring HTTPS On AWS Application Load Balancer

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) ![https://img.shields.io/badge/%20-EC2-blue](https://img.shields.io/badge/%20-Ec2-blue) ![https://img.shields.io/badge/%20-HTTPS-blue](https://img.shields.io/badge/%20-HTTPS-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue)|

## Lab Scenario

In this lab, you will configure HTTPS on AWS Application Load Balancer. You will use self-signed certificates for configuring HTTPS on the AWS Application Load Balancer and verify that the back end targets can be accessed via HTTPS.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Configure HTTPS on AWS Application Load Balancer using self-signed certificate
- Test the access to the back end targets using HTTPS.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- An AWS Account used to access AWS Management Console.
- You will need to create a self-signed certificate following the instructions from [Creating a Self-Signed Certificate on MacOS X](../general/creating-self-signed-cert-on-macos.md) or [Creating a Self-Signed Certificate on Windows 10](../general/creating-self-signed-cert-on-windows.md) depending on the operating system you use.
- You will need to create the AWS Application Load Balancer infrastructure by following the instructions from [Creating an Application Load Balancer in AWS](../../networking-labs/aws/creating-application-load-balancer-in-aws.md).

## Lab Instructions

### Exercise #1: Create a Self-Signed Certificate to Use for the Application Load Balancer

In this exercise you will create a self-signed certificate that you will use for the Application Load Balancer.

1. Use the inststructions from [Creating a Self-Signed Certificate on MacOS X](../general/creating-self-signed-cert-on-macos.md) or [Creating a Self-Signed Certificate on Windows 10](../general/creating-self-signed-cert-on-windows.md) to create a self-signed certificate.
2. Notice the folder on your local machine where the certificate files are saved.

### Exercise #2: Create the Infrastructure for the AWS Application Load Balancer

In this exercise you will create the infrastructure for the AWS Application Load Balancer.

1. Use the instructions from [Creating an Application Load Balancer in AWS](../../networking-labs/aws/creating-application-load-balancer-in-aws.md) to create the infrastructure for the Application Load Balancer.
2. Verify that the back end targets are accessible using the HTTP (80) port using the Application Load Balancer's DNS name.

### Exercise #3: Add an HTTPS Listener in AWS Application Load Balancer

In this exercise, you will add an HTTPS Listener in the Application Load Balancer in Amazon AWS.

1. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
2. In the search box on top of the screen, type *EC2* and press *Enter*.
3. Click on *EC2* from the list of *Services*.
4. On the new page, scroll down the left-hand navigation and find section *Load Balancing*.
5. Click on the *Load Balancers*.
6. Find the `[initials]-networkinglab-ec2-lb` load balancer, and click on it.
7. Click on the *Listeners* tab for the load balancer.
8. Click on the [Add listener button](media/aws-add-listener-blue-button.png) button to add a new listener.
9. On the *Add listener* page, fill in the following information:
  - *Protocol: port* → HTTPS:443
10. Click on the [Add action button](media/aws-add-action-dropdown-button.png) button under *Default action(s)* and select `Forward to...`.
11. Select `[initials]-networkinglab-web-instances` from the *Target group* list.
12. Click on the [Confirm button](media/aws-confirm-check-button.png) button to confirm your selection.
13. Select `Import` for the *Default SSL certificate* field.
14. Select the `IAM` radio button in the *Import to* section.
15. Type the following name in the *Certificate name* input field:
  ```
  [your_name]-self-signed-certificate
  ```
16.  Find the `[your_name]-self-signed.decrypted.key` key file that you created as part of the *exercise #1*, and open it with a text editor.
17.  Copy the content of the *private key* and paste it in the *Certificate private key (PEM encoded)* input field.
18.  Find the `[your_name]-self-signed.key` certificate file that you created as part of the *exercise #1*, and open it with a text editor.
19.  Copy the content of the *certificate* and paste it in the *Certificate body (PEM encoded)* input field.
    
    > **Note:** Make sure that you do not modify the content of the file
20. Click on the [Add listener button](media/aws-add-listener-blue-button.png) button to save the new listener.
21. Click on the [Back button](media/aws-back-button.png) button to go back to the list of load balancers.

#### Exercise Summary

At this point, you have learned how to create a new HTTPS listener in the Application Load Balancer in Amazon AWS.

### Exercise #2: Configure the Security Group to Allow HTTPS Traffic and Disable HTTP Traffic

In this exercise, you will configure the Security Group used by the Application Load Balancer to allow secure HTTPS traffic and disable non-secure HTTP traffic.

1. Click on the *Description* tab for the Application Load Balancer.
2. Scroll down to the *Security* section.
3. Click on the *security group* used for the load balancer.
4. Change to the *Inbound rules* tab for the security group.
5. Click on the [Edit inbound rules button](media/aws-edit-inbound-rules-button.png) button.
6. Click on the [Add rule button](media/aws-add-rule-button.png) button.
7. Select the following options:
   - *Type* → `HTTPS`
   - *Source* → `Custom` `0.0.0.0/0`
8. Click on the [Save rules button](media/aws-save-rules-orange-button.png) button to save the rules.

#### Exercise Summary

At this point, you have learned how to configure the security group used by the Application Load Balancer to allow HTTPS traffic and disable HTTP traffic.

### Exercise 3: Test the HTTPS Access to the Target Group Web Servers

In this exercise you will verify the backend target group web servers can be accessed via HTTPS.

1. Scroll down the left-hand navigation and find section *Load Balancing*.
5. Click on the *Load Balancers*.
6. Find the `[initials]-networkinglab-ec2-lb` load balancer, and click on it.
7. From the *Description* tab for the Application Load Balancer, copy the *DNS name*.
8. Open a new browser window and type `https://` in the address line, paste the *DNS name* after that, and press *Enter*.
9. You will see a browser warning. Add the URL to your browser's exception list and load the page.
10. Click next to the lock icon in the browser's address line and click on *More information*.
11. Click on the *View certificate* to view the certificate.

#### Exercise Summary

At this point, you have learned how to test the HTTPS configuration for your Applicaiton Load Balancer and view the certificate in the browser.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)