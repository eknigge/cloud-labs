# Configuring HTTPS On Azure Application Gateway

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Microsoft Azure**        |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Applicaiton%20Gateway-blue](https://img.shields.io/badge/%20-Applicaiton%20Gateway-blue) ![https://img.shields.io/badge/%20-Certificates-blue](https://img.shields.io/badge/%20-Certificates-blue) ![https://img.shields.io/badge/%20-HTTPS-blue](https://img.shields.io/badge/%20-HTTPS-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue)|

## Lab Scenario

In this lab, you will configure HTTPS on Azure Application Gateway. You will use self-signed certificates for configuring HTTPS on the Azure Application Gateway and verify that the back end targets can be accessed via HTTPS.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Configure HTTPS on Azure Application Gateway using self-signed certificate
- Test the access to the back end targets using HTTPS.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- A Microsoft Azure Account used to access Azure Portal.
- You will need to create a self-signed certificate following the instructions from [Creating a Self-Signed Certificate on MacOS X](../general/creating-self-signed-cert-on-macos.md) or [Creating a Self-Signed Certificate on Windows 10](../general/creating-self-signed-cert-on-windows.md) depending on the operating system you use.
- You will need to create the Azure Application Gateway infrastructure by following the instructions from [Creating an Azure Application Gateway](../../networking-labs/azure/creating-application-gateway-in-azure.md).

## Lab Instructions

### Exercise #1: Create a Self-Signed Certificate to Use for the Application Load Balancer

In this exercise you will create a self-signed certificate that you will use for the Application Load Balancer.

1. Use the inststructions from [Creating a Self-Signed Certificate on MacOS X](../general/creating-self-signed-cert-on-macos.md) or [Creating a Self-Signed Certificate on Windows 10](../general/creating-self-signed-cert-on-windows.md) to create a self-signed certificate.
2. Notice the folder on your local machine where the certificate files are saved.

### Exercise #2: Create the Infrastructure for the Azure Application Gateway

In this exercise you will create the infrastructure for the Azure Application Gateway.

1. Use the instructions from [Creating an Azure Application Gateway](../../networking-labs/azure/creating-application-gateway-in-azure.md) to create the infrastructure for the Application Load Balancer.
2. Verify that the back end targets are accessible using the HTTP (80) port using the Application Load Balancer's Public IP address.

### Exercise #3: Add an HTTPS Listener in Azure Application Gateway

In this exercise, you will add an HTTPS Listener in the Application Gateway in Microsoft Azure.

1. Sign into the Microsoft Azure Management Portal at [http://portal.azure.com]http://portal.azure.com using your Microsoft Account.
2. Click on the ![Resource groups button](media/azure-resource-groups-button.png) button button in the left-hand menu list under the Microsoft Azure logo.
3. Find the `aznetworkinglab-[initials]-rg` resource group in the list and click on it.
4. Find the `aznetworkinglab-[initials]-ag` Applicatino Gateway resource and click on it.
5. Click on the ![Listeners button](media/azure-listeners-button.png) in the second-level navigation in the *Settings* section.
6. Click on the ![Add listener button](media/azure-add-listener-plus-button.png) button to add new listener.
7. Fill in the following information:
   - *Listener name* → `https_listener`
   - *Frontend IP* → `Public`
   - *Port* → `443`
   - *Protocol* → `HTTPS`
   - *Choose a certificate* → `Upload a certificate`
   - *Cert name* → `[your_name]-self-signed-cert`
8. Click on the ![Folder button](media/azure-folder-icon-button.png) icon next to the *CER certificate* field.
9. Select the `[your_name]-self-signed.key.pfx` certificate file that you created in the *Creating a Self-Signed Certificate* lab.
10. Type the password for the private key in the *Password* field.
11. Click on the ![Add button](media/azure-add-button.png) button to add the listener.
12. Click on the ![Rules button](media/azure-rules-button.png) in the second-level navigation in the *Settings* section.
13. Click on the ![Request routing rule](media/azure-request-routing-rule-plus-button.png) button to add a rule.
14. Fill in the following information:
   - *Rule name* → `aznetworkinglab-[initials]-ag-rule02`
   - *Listener* → `https_listener`
15. Switch to the *Backend targets* tab and fill in the following information:
   - *Target type* → `Backend pool`
   - *Backend target* → `aznetworkinglab-[initials]-ag-bepool`
   - *HTTP settings* → `aznetworkinglab-[initials]-ag-http-setting`
16. Click on the ![Add button](media/azure-add-button.png) button to add the routing rule.
17. Click on the ![Overview button](media/azure-overview-button.png) in the second-level navigation and copy the *Frontend public IP address* of the Application Gateway.
18. Open a new browser window, paste the copied IP address in the address bar and presee the *Enter* key.
19. If you see a warining in your browser add it to the exception to continue loading the page and load the page.
20. Click on the *lock* icon next to the `https` in the browsers address bar.
21. Find the *View Certificate* option and eaxamine the certificate. Depending on the browser you use finding that option may few clicks.

#### Exercise Summary

At this point, you have learned how to test the HTTPS configuration for your Applicaiton Gateway in Azure and view the certificate in the browser.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)