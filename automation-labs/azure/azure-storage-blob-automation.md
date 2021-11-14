# Azure Storage Blob Automation

> Hands-on Lab

|                     |                       |
| :------------------ | :-------------------- |
| *Cloud Vendor*      | **Microsoft Azure**   |
| *Proficiency Level* | **Cloud  Enthusiast** |
| *Tags*              | ![https://img.shields.io/badge/%20-Automation-blue](https://img.shields.io/badge/%20-Automation-blue) ![https://img.shields.io/badge/%20-Storage-blue](https://img.shields.io/badge/%20-Storage-blue) |

## Lab Scenario
In this lab, you will provision a Microsoft Azure Storage blob using Azure CLI and an Azure Resource Manager (ARM) template.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Install Azure CLI
- Sign into Azure using the CLI and your credentials
- Provision an Azure Storage blob using ARM template

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection
- A work, school or personal Microsoft Account used to access Microsoft Azure Management Portal
- A subscription for Microsoft Azure

## Exercises

### Exercise #1: Install Azure CLI and Sign Into Azure

In this exercise, you will install Azure CLI on your machine and sign into Azure using your credentials.

1. Download and install the latest version of Azure CLI from [this page](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).
2. Sign into Azure using the following command:
   ```
   az login
   ```
3. Make sure the default account is set to your preferred subscription using the following command:
   ```
   az account show
   ```
4. If needed set your subscription using the following command:
   ```
   az account set -s [subscription_id]
   ```
   where `subscription_id` is your subscription ID.

#### Exercise Summary
At this point, you have learned how to install Azure CLI and use it to sign into Azure.

### Exercise #2: Install Azure CLI and Sign Into Azure

In this exercise, you will install Azure CLI on your machine and sign into Azure using your credentials.

1. Download the ARM [template.json](template.json) to a folder on your local machine.
2. Using terminal window, create an Azure resource group using the following command:
   ```
   az group create --name azautomationlab-[initials]-rg --location "West US 2"
   ```
3. Deploy the template using the following command:
   ```
   az deployment group create --name [your_initials]Deployment --resource-group azautomationlab-[initials]-rg --template-file template.json --parameters storageAccount_name="[your_initials]usw2str" owner_name="[your_first_and_last_names]" owner_email="[your_email_address]"
4. Sign into the Microsoft Azure Management Portal at [http://portal.azure.com](http://portal.azure.com) using your Microsoft Account and verify that the storage account is created.

#### Exercise Summary
At this point, you have learned how to deploy a new Azure Storage blob using an ARM template.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)