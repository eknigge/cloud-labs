# Azure VM With Ubuntu and NGINX Web Server &middot;

> Hands-on Lab

|                   |                   |
| :---------------- | :---------------- |
| Cloud Vendor      | Microsoft Azure   |
| Proficiency Level | Cloud  Enthusiast |
| Tags              | ![https://img.shields.io/badge/%20-Linux-blue](https://img.shields.io/badge/%20-Linux-blue) ![https://img.shields.io/badge/%20-NGINX-blue](https://img.shields.io/badge/%20-NGINX-blue) ![https://img.shields.io/badge/%20-Ubuntu-blue](https://img.shields.io/badge/%20-Ubuntu-blue) ![https://img.shields.io/badge/%20-Virtual%20Machine-blue](https://img.shields.io/badge/%20-Virtual%20Machine-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue) |

## Lab Scenario
In this lab, you will provision a Microsoft Azure Virtual Machine (VM) that runs Ubuntu Linux server operating system. Once the VM is provisioned, you will install a NGINX Web server software on it. After the Web server is installed, you will verify that it is running by accessing its home page with a browser. Last, you will modify the home page to show the text `Hello, computelabadmin!`

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

1. Sign into the Microsoft Azure Management Portal at http://portal.azure.com using your Microsoft Account.
2. Click on ![Create a resource](media/azure-create-a-resource.png) in the upper left corner right under the logo.
3. In the search box search for Ubuntu Server 20.04.
4. Select Ubuntu Server 20.04 LTS by Canonical from the list of results.
5. Click on the ![Create button](media/azure-create-button.png) button.
6. On the *Basics* tab in section, *Project Details* fill in the following information:
  - *Subscription* → `[select your Microsoft Azure subscription]`
  - *Resource group* → `Create new`
  - *Resource group name* (the text field in the pop up) → `azvmnginxlab-[initials]-rg`, where `[initials]` are your first, middle, and last name initials
7. On the *Basics* tab in section, *Instance Details* fill in the following information:
  - *Virtual machine name* → `azvmnginxlab-[initials]-vm01`
  - *Region* → `West US 2`
  - *Availability options* → `No infrastructure redundancy required`
  - *Image* → `Ubuntu Server 20.04 LTS`
  - *Size* → Click on **See all sizes** and select `B1s` then click on the ![Select button](media/azure-select-button.png) button

  > If the VM size is not available for selection, try changing the region.
8. On the *Basics* tab in section, *Administrator Account* fill in the following information:
  - *Authentication type* → `Password`
  - *Username* → `computelabadmin`
  - *Password* → `[type a strong password]`
  - *Confirm password* → `[type the same password as above]`

### Exercise 2: Exercise Title
### Exercise 3: Exercise Title

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)