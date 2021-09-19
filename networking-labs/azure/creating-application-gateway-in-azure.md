# Creating An Application Gateway In Microsoft Azure

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Microsoft Azure**   |
| Proficiency Level | **Cloud Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Application%20Gateway-blue](https://img.shields.io/badge/%20-Application%20Gateway-blue) ![https://img.shields.io/badge/%20-Load%20Balancer-blue](https://img.shields.io/badge/%20-Load%20Balancer-blue) ![https://img.shields.io/badge/%20-Web%20Server-blue](https://img.shields.io/badge/%20-Web%20Server-blue)|

## Lab Scenario
In this lab, you will provision an Application Gateway in Microsoft Azure. You will configure the Application Gateway to balance web traffic between two web servers deployed on Microsoft virtual machines.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Provision an Application Gateway in Microsoft Azure.
- Configure the Application Gateway to balance web traffic between Virtual Machines.

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection.
- A work, school or personal Microsoft Account used to access Microsoft Azure Management Portal.
- A subscription for Microsoft Azure.
- You will need to create a virtual network with two subnets following the [Creating Virtual Network And Subnets In Azure](creating-virtual-network-and-subnets-in-azure.md) lab. You must follow the steps described in that lab to create and configure the virtual network.
- You will need to create two virtual machines following the [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab. You must follow the steps described in that lab to create and configure the two virtual machines. However some modifications for each instance will be required. Those will be described in the exercises below. 

## Exercises

### Exercise #1: Create a Virtual Network to Host the Virtual Machines and the Application Gateway

In this exercise you will provision the virtual network that will host the virtual machines and the aplication gateway. 

1. Follow the instructions in the [Creating Virtual Network And Subnets In Azure](creating-virtual-network-and-subnets-in-azure.md) lab to create the virtual network with two subnets.

#### Exercise Summary

At this point, you have rected a virtual network that will host the virtual machines and the Application Gateway.

### Exercise #2: Provision the First Virtual Machine

In this exercise you will provision the first virtual machine that will be connected to the Application Gateway. Follow the instructions in the [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab with the following modifications:

1. In *step 6* of *exercise #1*, instead creating a new resource group, select the existing one you created for the virtual network:
   - `aznetworkinglab-[initials]-rg`, where `[initials]` are your first, middle, and last name initials
2. In *step 9* of *exercise #1*, in addition to the `HTTP (80)` and `SSH (22)` select `HTTPS (443)` in *Selected inbound ports*.
3. In *step 13*, instead using the default selections for networking, select the following values:
   - *Virtual network* → `aznetworkinglab-[initials]-vnet`
   - *Subnet* → `private`

### Exercise #2: Install NGINX Web Server on the First Virtual Machine and Modify its Home Page

In this exercise you will connect the first EC2 instance, install the NGINX web server and modify its home page. Follow the instructions in the [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab with the following modifications:

1. Follow *exercise #2* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to connect to the first virtual machine.
2. Follow *exercise #3* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to install the NGINX web server.
3. Follow *exercise #5* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to modify the web server's home page.
4. In *step 4* of *exercise #5* use the following HTML code:
   ```
   Hello, <code>I am virtual machine #1</code>!
   ```

### Exercise #3: Provision the Second Virtual Machine

In this exercise you will provision the second virtual machine that will be connected to the Application Gateway. Follow the instructions in the [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab with the following modifications:

1. In *step 6* of *exercise #1*, instead creating a new resource group, select the existing one you created for the virtual network:
   - `aznetworkinglab-[initials]-rg`, where `[initials]` are your first, middle, and last name initials
2. In *spet 7* of *exercise #1* use the following name for the virtual machine:
   - *Virtual machine name* → `azvmnginxlab-[initials]-vm02`
3. In *step 9* of *exercise #1*, in addition to the `HTTP (80)` and `SSH (22)` select `HTTPS (443)` in *Selected inbound ports*.
4. In *step 13*, instead using the default selections for networking, select the following values:
   - *Virtual network* → `aznetworkinglab-[initials]-vnet`
   - *Subnet* → `private`

### Exercise #4: Install NGINX Web Server on the Second Virtual Machine and Modify its Home Page

In this exercise you will connect the second EC2 instance, install the NGINX web server and modify its home page. Follow the instructions in the [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab with the following modifications:

1. Follow *exercise #2* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to connect to the second virtual machine.
2. Follow *exercise #3* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to install the NGINX web server.
3. Follow *exercise #5* from [Azure VM With Ubuntu and NGINX Web Server](../../compute-labs/azure/azure-vm-with-ubuntu-and-nginx-web-server.md) lab to modify the web server's home page.
4. In *step 4* of *exercise #5* use the following HTML code:
   ```
   Hello, <code>I am virtual machine #2</code>!
   ```

### Exercise #5: Provision an Application Gateway in Microsoft Azure

In this exercise, you will provision an Application Gateway in Microsoft Azure. The Gateway will be provisioned in the already created virtual network and use the virtual machines as backend pool.

1. Sign into the Microsoft Azure Management Portal at [http://portal.azure.com](http://portal.azure.com) using your Microsoft Account.
2. Click on ![Create a resource](media/azure-create-a-resource.png) in the upper left corner right under the Microsoft Azure logo.
3. In the search box search for *Application Gateway*.
4. Select *Application Gateway* from the list of results.
5. Click on the ![Create button](media/azure-create-button.png) button.
6. On the *Basics* tab in section, *Project Details* fill in the following information:
  - *Subscription* → `[select your Microsoft Azure subscription]`
  - *Resource group* → `aznetworkinglab-[initials]-rg`, where `[initials]` are your first, middle, and last name initials
7. On the *Basics* tab in section, *Instance Details* fill in the following information:
  - *Application gateway name* → `aznetworkinglab-[initials]-ag`, where `[initials]` are your first, middle, and last name initials
  - *Region* → `West US 2`
  - *Tier* → `Standard V2`
8. On the *Basics* tab in section, *Configure Virtual Network* fill in the following information:
  - *Virtual network* → `aznetworkinglab-[initials]-vnet`
  - *Subnet* → `public`
9. Click on the ![Next : Frontends button](media/azure-next-frontends-button.png) button.
10. On the *Frontends* tab, fill in the following information:
  - *Frontend IP address type* → `Public`
  - *Public IP address* → click on `Add new`
11. In the *Add a public IP* form, fill in the following information:
  - *Name* → `aznetworkinglab-[initials]-ag-ip`
12. Click on the ![OK button](media/azure-ok-button.png) button.
13. Click on the ![Next : Backends button](media/azure-next-backends-button.png) button.
14. Click on the *Add a backend pool* and fill in the following information:
  - *Name* → `aznetworkinglab-[initials]-ag-bepool`
  - *Target type* → `Virtual machine`
15. Select the `aznetworkinglab-[initials]-vm01` and `aznetworkinglab-[initials]-vm02` in two separate rows with *Target type* → `Virtual machine`.
16. Click on the ![Add button](media/azure-add-button.png) button.
17. Click on the ![Next : Configuration button] button.
18. Click on *Add a routing rule* and fill in the following information:
  - *Rule name* → `aznetworkinglab-[initials]-ag-rule01`
  - *Listener name* → `http_listener`
  - *Frontend IP* → `Public`
  - *Protocol* → `HTTP`
  - *Port* → `80`
19. Switch to the *Backend targets* tab and fill in the following information:
  - *Target type* → `Backend pool`
  - *Backend target* → `aznetworkinglab-[initials]-ag-bepool`
  - *HTTP settings* → click on `Add new`
21. In the *Add a HTTP setting* form, fill in the following information:
  - *HTTP settings name* → `aznetworkinglab-[initials]-ag-http-setting`
22. Click on the ![Add buton](media/azure-add-button.png) button.
23. Click on the ![Add buton](media/azure-add-button.png) button.
24. Click on the ![Next : Tags button](media/azure-next-tags-button.png) button.
25. On the *Tags* tab, fill in the following information:
  - *Role* → `application gateway`
  - *Lab* → `aznetworkinglab`
  - *Owner* → `[your full name]`
  - *OwnerEmail* → `[your email address]`
26. Click on the ![Next : Review + create button](media/azure-next-review-and-create-button.png) button.
27. Review your configuration and click on the ![Create button](media/azure-create-button.png) button.
16. Wait until the deployment is completed.
17. Once the deployment is complete, click on the ![Resource groups button](media/azure-resource-groups-button.png) button in the left-hand menu list under the Microsoft Azure logo.
24. Find the `aznetworkinglab-[initials]-rg` resource group in the list and click on it.
25. Verify the following resource types exist:
    - `Application gateway`

#### Exercise Summary

At this point, you have learned how to provision and configure an Application Gateway in the Microsoft Azure cloud. Note that although you requested the creation of a single resource, multiple were created.

### Exercise #6: Testing an Application Gateway in Microsoft Azure

In this exercise, you will test the Application Gateway that you created in Microsoft Azure. You can test the Application Gateway by accessing its IP address from a browser.

1. Click on the `aznetworkinglab-[initials]-ag` Application Gateway resource.
2. In the *Overview* tab, note the *Frontend public IP address*.
3. Open a new browser window, and paste the above IP address in the address bar.
4. The page shows the home page of the NGINX server on `azvmnginxlab-[initials]-vm01`.
5. Refresh the page in the browser.
6. The page shows the home page of the NGINX server on `azvmnginxlab-[initials]-vm02`.

#### Exercise Summary

At this point, you have learned how to test the Application Gateway in the Microsoft Azure cloud.

### Exercise #7: Delete the Resources

In this exercise you will delete all resources to save on cost.

1. Click on the ![Resource groups button](media/azure-resource-groups-button.png) button in the left-hand menu list under the Microsoft Azure logo.
2. Find the `aznetworkinglab-[initials]-rg` resource group in the list and click on it.
3. Click on the ![Delete resource group button](media/azure-delete-resource-group-button.png) button.
4. Type the resource group name and click on the ![Delete button](media/azure-delete-button.png) button.

#### Exercise Summary

At this point, you have learned how to delete all resources in the resource group and save cost.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)