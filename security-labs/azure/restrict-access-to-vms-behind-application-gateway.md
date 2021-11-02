# Restrict Access to the VMs Behind Azure Application Gateway

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Microsoft Azure**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Applicaiton%20Gateway-blue](https://img.shields.io/badge/%20-Applicaiton%20Gateway-blue) ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) ![https://img.shields.io/badge/%20-HTTPS-blue](https://img.shields.io/badge/%20-HTTPS-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue)|

## Lab Scenario

In this lab, you will restrict the access to the VMs behind an Azure Application Gateway by modifying the firewall rules on each individual VM.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Specify inbound rules for Network Security Groups in Azure. 
- Test the access to the back end VMs.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- A Microsoft Azure Account used to access Azure Portal.
- You will need to create the Azure Application Gateway infrastructure by following the instructions from [Configuring HTTPS On Azure Application Gateway](configuring-https-on-azure-application-gateway.md).

## Lab Instructions

### Exercise #1: Configure HTTPS On Azure Application Gateway

In this exercise you will configure HTTPS on Azure Application Gateway.

1. Use the instructions from [Configuring HTTPS On Azure Application Gateway](configuring-https-on-azure-application-gateway.md) to configure HTTPS on Azure Application Gateway.
2. Verify that the back end targets are accessible using the HTTP (80) and HTTPS (443) ports using the Application Gateway's Public IP address.

### Exercise #2: Restrict the HTTP Access ot the Backend VMs to the Application Gateway Only

In this rxercise you will restrict the HTTP Access to the backend VMs to Azure Application Gateway only. This will prevent direct HTTP access to the VMs.

1. Sign into the Microsoft Azure Management Portal at [http://portal.azure.com]http://portal.azure.com using your Microsoft Account.
2. Click on the ![Resource groups button](media/azure-resource-groups-button.png) button button in the left-hand menu list under the Microsoft Azure logo.
3. Find the `aznetworkinglab-[initials]-rg` resource group in the list and click on it.
4. Find the `azvmnginxlab-[initials]-vm01` virtual machine and click on it.
5. Click on the ![Azure networking button](media/azure-networking-button.png) in the second-level navitation in the *Settings* section.
6. Click on the ![Three dots](media/azure-three-dots-button.png) at the end of the `HTTPS` row and delete the row.
7. Click on the `HTTP` row and change the following settings:
   - *Source* → `Service Tag`
   - *Source service tag* → `AzureLoadBalancer`
8. Click on the ![Save button](media/azure-save-button.png) to save the changes.
9. Copy the *NIC Public IP* address for the VM.
10. Open a new browser window, paste the IP address in the address bar and press Enter. You should see timeout for the page.
11. Repeat *steps 4-10* for the `azvmnginxlab-[initials]-vm02` virtual machine.
12. Click on the ![Resource groups button](media/azure-resource-groups-button.png) button button in the left-hand menu list under the Microsoft Azure logo.
13. Find the `aznetworkinglab-[initials]-rg` resource group in the list and click on it.
14. Find the `aznetworkinglab-[initials]-ag` Applicatino Gateway resource and click on it.
15. Copy the *Frontend public IP address* of the Application Gateway from the *Overview* page.
16. Open a new browser window, paste the IP address in the address bar and press Enter. You should see the home page of the web server running on one of the VMs.
17. Refresh the page until you see the home page of the web server running on the other VM.

#### Exercise Summary

At this point, you have learned how to restrict the access to the backend VMs and verify that the Application Gateway in Azure can still serve the pages using HTTPS.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)