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

- Set up a Domain Controller & set up Client-1 in Azure
- Set the Domain Controller's NIC Private IP to be Static
- Change DNS and NIC to point to DC-1's Private IP Address
- In PowerShell run both "ping" & "ipconfig/all" and view the results. 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="" height="80%" width="80%" alt="Set up Domain Controller in Azure"/>
</p>
<p>
In Azure, create a new Resource Group named "Active-Directory-Lab", create a Virtual Network named "Active-Directory-Vnet" **Set the resource group to be the "Active-Directory-Lab**, & create a new Virtual Machine named "DC-1". 
<br />**Resource Group needs to be Active-Directory-Lab** 
<br /> **Image needs to be Windows Server 2022 Datacenter: Azure Edition**. 
<br /> Once those have been created, select the "networking Tab" and select V-Net to be the one we created, "Active-Directory-Vnet". Once the above steps have been completed, select Review & Create. Create a new Virtual Machine named "Client-1", for the Image select Windows 10 Pro. Select the "networking" tab and select the Active-Directory-Vnet", and review & Create.  
</p>
<br />

<p>
<img src="https://i.imgur.com/y3UkPzz.png" height="80%" width="80%" alt="Set the Domain Controller's NIC Private IP to be Static"/>
</p>
<p>
Navigate to the Virtual Machines and select the DC-1 we created in step 1. Follow this path to find NIC settings: Networking --> Networking Settings --> DC-1190_z1 | IP Configurations --> ipconfig1 
Select the Static option under "Private IP Address Settings". For testing purposes of the lab, we are going to disable the firewall of DC-1. Find DC-1's IP and connect to the machine. Once logged in, Right click the start menu and open the "Run" action. and type "wf.msc" to open "Windows Defender Firewall With Advanced Security". From here, locate the option "Windows Defender Firewall Properties" And for "Firewall State" Select OFF and hit APPLY. 
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt="Change DNS And NIC to point to DC-1's Private IP Address"/>
</p>
<p>
Navigate to DC-1 in Virtual Machines in Azure. and locate and copy DC-1's Private IP Address. Once copy navigate back to Client-1 and follow this path: Networking --> Networking Settings --> Client-1178 z1 Primary --> DNS Servers. From here, select the option "Custom" and paste in the DC-1's private IP that we located at the beginning of this step. Once completed, go back to Virtual Machines and restart "Client-1".    
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt=""/>
</p>
<p>
Now that these settings have been applied, we can log in to "Client-1" VIA Remote Desktop Connection. Once logged in, launch "Windows PowerShell as administrator" and type "Ping 10.0.0.4". Ensure the ping to DC-1 was successful. In PowerShell, run "ipconfig/all". If done correctly, the DNS settings should show DC-1's private address. 
</p>
<br />
