<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Preparing Active Directory Infrastructure in Azure
- Deploying Active Directory 
- Creating Users with PowerShell
- Group Policy and Managing Accounts 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/UVvFbkl.png" height="80%" width="80%" alt="Preparing AD Infrastructure in Azure"/>
</p>
<p>
To start in Azure, create a Resource Group, name the Resource Group "Active-Directory-Lab", and place it into "East US 2". Next, create a new Virtual Network. Make this Virtual Networks resource group the one we had just created, "Active-Directory-Lab". Name the Virtual Network "Active-Directory-Vnet", as well as placing it in "East US 2", than review and create. Now, create a new Virtual Machine. For the new Virtual Machine, select the new Resource Group we created, "Active-Directory-Lab", and name the Virtual Machine dc-1 select the same region as before, "East US 2". **IMPORTANT STEP** Make sure you have Windows Server 2022 Datacenter Azure Edition selected for "Image". Size can be anything as long as it has 2 CPUs. For the lab, we will use the Username: labuser & Password: Cyberlab123!. Next in the Networking tab. Select the "Active-Directory-Vnet", and we can review and create. 
<br /> 
<img src="https://i.imgur.com/LujMUo7.png" height="80%" width="80%" alt="Preparing AD Infrastructure in Azure"/>
<br />
Now, create another Virtual Machine. Select "Active-Directory-Lab" for the Resource group. and name the Virtual machine "Client-1". For image select "Windows 10 Pro", for Size select "Standard_d2s_2 2 CPUs". For the Username and Password, use the same as we did prior: Username: labuser & Password: Cyberlab123!. Now, in the "Networking" tab, place it into the "Active-Directory-Vnet" and you can review and create. Once both have been deployed, navigate back into the Virtual Machine and select dc-1. In dc-1, select: Networking Settings --> Network Interface / IP Configuration --> ipconfig1 --> Allocation
Change from "Dynamic" to "Static". 
<br /> 
<img src="https://i.imgur.com/tFz1jVM.png" height="80%" width="80%" alt="Preparing AD Infrastructure in Azure"/>
<br /> 
Locate the dc-1 public IP Address and connect into dc-1. Once logged in right right-click the start menu and launch "Run" once opened, type "wf.msc" to open "Windows Defender Firewall" and disable the firewall off by locating "Properties". 
<br /> 
<img src="https://i.imgur.com/eYiVH7Q.png" height="60%" width="60%" alt="IPCONFIG"/>
  <img src="https://i.imgur.com/ZXUzX7u.png" height="60%" width="60%" alt="PING"/>
<br />  
Back into Azure, locate dc-1's private IP Address. Now navigate to "Client-1" and follow this path: Virtual Machines --> Client-1 --> Networking Settings --> Network Interface / IP Configuration --> DNS Servers. Change "Inherit from virtual Network" to "Custom" and paste in dc-1's Private IP address and save. From Azure, restart Client-1 by going into "Virtual Machines" and selecting "Restart". 
Once Client-1 has been restarted, copy Client-1's Public IP address and "Remote Desktop Connection" into Client-1. In Azure, select "Virtual Machine" and select and copy dc-1's private IP Address so we can test "ping" on our client-1 machine. Back into the client-1 Virtual Machine, in the search bar, search "PowerShell" and launch. From here, you can type "ping" and paste in dc-1's private IP (For example, 10.0.0.4). If successful and no "timeout errors" occur, we can run in PowerShell "ipconfig /all". If the above steps have been completed correctly, you should see dc-1's private IP Address being displayed under "DNS Servers . . . . . 10.0.0.4". 
<p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Deploying Active Directory"/>
</p>
<p>
TEXT GOES HERE 
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Creating Users with PowerShell"/>
</p>
<p>
TEXT GOES HERE 
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Group Policy and Managing Accounts"/>
</p>
<p>
TEXT GOES HERE 
</p>
<br />
