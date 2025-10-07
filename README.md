<p align="center">
<img src="https://github.com/user-attachments/assets/994e5afb-bec5-4370-8cdd-aa1da7c30dcb" />
</p>
</p>

<h1>Preparing AD Infrastructure in Azure</h1>
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

- Create a Resource Group
- Create a Virtual Network and Subnet
- Create the Domain Controller VM (Windows Server 2022)
- Set dc-1 NIC Private IP address to be static
- Disable the Windows Firewall (for testing connectivity)
- Create the Client VM (Windows 10)
- Set region and Virtual Network same as DC-1
- Set Client-1’s DNS settings to DC-1’s Private IP address
- From the Azure Portal, restart Client-1
- Ping DC-1’s private IP address
- Ensure the ping succeeded
- Open PowerShell and run ipconfig /all
- DNS settings should show DC-1’s private IP Address

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/e7bbd916-aaab-4319-ba99-b71104f8a810" />
</p>
<p>

</p>
<br />
