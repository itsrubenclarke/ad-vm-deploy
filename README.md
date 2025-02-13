<p align="center">
<img src="https://github.com/user-attachments/assets/ea8315b8-28f8-4d0a-a370-917bdc1c56f3" height="30%" width="50%" alt="Microsoft Azure Logo"/>
</p>

<h1>Active Directory: Virtual Machine Deployment</h1>

<p>
This project is the second amongst a collection focused on implementing Azure and Active Directory. 
Microsoft Azure is a cloud platform that will let you rent space to store or process your own data.
In this project, I will set up and establish a connection between two virtual machines using Windows 10 Pro and Windows Server 2022 in Microsoft Azure's Cloud environment. 
</p>

<h2>Key Objectives</h2>
<h3>Virtual Machine Setup</h3>

-  Configure and deploy Windows Client
-  Configure and deploy Windows Domain Controller

<p>
  <h3>Remote Connectivity</h3>
  
  - Establish Remote Desktop Connection (RDP)
  - Connect Client and Domain Controller Virtual Machines (VMs)
</p>

<h3>Environments and Technologies Used</h3>

- Microsoft Azure (Virtual Machines, Networking)
- Windows App (Remote Desktop Protocol)
- PowerShell (Command-line Operations)

<p>
  <h3>Operating Systems Used</h3>
</p>

| **Operating System**        | **Role**               
|----------------------------|------------------------|
| <img alt= "windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20"> Windows (Windows 10 Pro) | Client VM |
| <img alt= "Windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20"> Windows (Server 2022) | Domain Controller (DC)             |


<h1>Setup and Configuration of Virtual Network</h1></p>

<h3>Step 1: Create Resource Group</h3>

- Go to [Portal.azure.com](https://portal.azure.com)
- Create a Resource Group
- Name it "Active-Directory-Lab" & Set the region to (Europe) UK South

<img width="831" alt="create resource group" src="https://github.com/user-attachments/assets/87b56d6d-77b3-4878-8444-ac645859c183" />

<h3>Step 2: Create Virtual Network</h3>

- Go to [Portal.azure.com](https://portal.azure.com)
- Create a Virtual Network
- Name it "Active-Directory-vnet" & Set the region to (Europe) UK South
- Add it to the "Active-Directory-Lab" Resource Group

<img width="811" alt="create virtual network" src="https://github.com/user-attachments/assets/4463a63b-3103-49d9-b455-bcefe4610e0b" />

<h3><img alt= "windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20">  Step 3: Setup Domain Controller</h3>

- Go to [Portal.azure.com](https://portal.azure.com)
- Create a Virtual Machine
- Select the "Windows Server 2022" image
- Name it "dc-1" & Set the region to (Europe) UK South
- Ensure to select the resource group you just created "Active-Directory-Lab"
- Select a vm size with at least 2 vcpus
- Set a username and password
- Be sure to memorise your credentials or store in a secure place
- Add the Virtual Machine to the Virtual Network you previously created in step 2 "Active-Directory-vnet"

<img width="798" alt="dc-01" src="https://github.com/user-attachments/assets/2c932191-d09f-4252-b957-030184e3314a" />
<img width="798" alt="credentials" src="https://github.com/user-attachments/assets/ec0c115f-b9c9-4714-87cb-c40f3dbf7bbd" />
<img width="863" alt="Virtual Network" src="https://github.com/user-attachments/assets/c6d0f8ad-ac57-4fa1-8c42-70a82d626c81" />


<h3><img alt= "windows logo" src="https://i.imgur.com/KcrV0u6.png" width="20">  Step 4: Setup Client VM</h3>

- Go to [Portal.azure.com](https://portal.azure.com)
- Create a Virtual Machine
- Select the "Windows 10 Pro" image
- Name it "client-1" & Set the region to (Europe) UK South
- Ensure to select the resource group you just created "Active-Directory-Lab"
- Select a vm size with at least 2 vcpus
- Set a username and password
- Be sure to memorise your credentials or store in a secure place
- Add the Virtual Machine to the Virtual Network you previously created in step 2 "Active-Directory-vnet"
- Tick the licensing request box

<img width="819" alt="client-1" src="https://github.com/user-attachments/assets/ac2c8b13-568e-4cbe-ab87-28b83a3b6e9f" />
<img width="763" alt="credentials" src="https://github.com/user-attachments/assets/da0c3f67-8003-43f2-8219-f27cd81df318" />

- Return to [Portal.azure.com](https://portal.azure.com)
- Search for "Virtual Machines"
- Confirm both client-1 and dc-1 Virtual Machines are running

<img width="813" alt="Vms Running" src="https://github.com/user-attachments/assets/c9f296aa-a447-4cb5-aea6-030ce78e7605" />

<h3>  Step 5: Network Interface Configuration</h3>
  
- Go to [Portal.azure.com](https://portal.azure.com)
- Select your "dc-1" Virtual Machine
- Open the Networking section and expand the Network Settings menu
- Open the configuration window

  <img width="909" alt="image" src="https://github.com/user-attachments/assets/e043f3df-e6b7-4848-9a87-029c4fa23f24" />

- Select "IP configurations"
- Select "ipconfig1"
- Edit the confgurations to change the Private IP address settings allocation from Dynamic to Static
  
<img width="813" alt="Dynamic" src="https://github.com/user-attachments/assets/a550235f-37a3-4372-998b-7315c4a7cb31" />

- Edit the confgurations to change the Private IP address settings allocation from Dynamic to Static
  
<img width="813" alt="Static" src="https://github.com/user-attachments/assets/dae33d5b-38ed-4b65-82a0-355014ef1d9b" />

<h3><img alt= "RDP logo" src="https://github.com/user-attachments/assets/4aaa5d6e-ce8b-481f-a8da-57edc9a2917e" width="20"> Step 6: Establish Remote Desktop Connection</h3>

- Launch your Remote Desktop Connection Application
    - Mac Users download <a href="https://apps.apple.com/us/app/windows-app/id1295203466?mt=12" target="_blank" rel="noopener noreferrer">Windows App</a> Formerly known as "Microsoft Remote Desktop"
    - Windows Users open and use Remote Desktop
- Select "Add PC"
- Choose "Add Credentials" from the drop down and enter the credentials you created earlier, noting to accept the security prompt and proceed
- You can now establish a remote connection to your virtual machine, by right-clicking the newly added device

