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
<img src="https://github.com/user-attachments/assets/9634332a-4ed0-4296-aa01-5621236f076a" />
/p>
<p>
Open Microsoft Azure create a new resource group.
</p>
<br />

<p>
 <img src="https://github.com/user-attachments/assets/f685fe68-31d3-40e3-9c52-d53e461e8321" />
</p>
<p>
Name the resource group and select the region.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/de97d33c-cd4e-4832-86e8-727f9e36df11" />
</p>
<p>
Review and create the resource group.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/b2f1673c-7659-440a-89b9-7b0ce6169b29" />
</p>
<p>
The resource group has been created succesfully.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/a81bd526-bb90-42bb-8912-bb42f3382f61" />
</p>
<p>
Next, search for "Virtual networks" to manually create the virtual network for the domain controller.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/a7e2dafa-8791-43b0-9b63-f0756825437b" />
</p>
<p>
While creating the virtual network, select the Active-Directory resource group and name the virtual network. Click "Review + Create"
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/b37c4a74-3bc7-4c24-81f6-b4a460937045" />
</p>
<p>
Go to Virtual Machines and rename the VM to DC-1 and make sure the reigon is the same as the Active-Directory resource group.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/665eabc6-6ca1-42f2-aef3-30d1951c8e02" />
</p>
<p>
Select the Windows Server 2022 Datacenter: Azure Edition- x64 Gen2, set the size to at least 2 cores with 8GB of memory, and if needed set to the correct Zone number.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/eb59ddaa-801e-4907-9278-660d94e8a684" />
</p>
<p>
In the Networking Tab select the Active-DirectoryVnet. Other settings should be left as is.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/e2782cf6-5547-4c2a-a939-02c3e3b13663" />
<p>
</p>
<p>
Review and create the domain controller vm.
</p>
<br />

<p>

<p>
<img src="https://github.com/user-attachments/assets/396202b1-a57f-410c-9738-1bdae66e3794" />
<p>
</p>
<p>
While DC-1 is in deployment, create another virtual machine for the client.

</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3ad8eef8-0b40-4107-bb1c-54fb05d13548" />
</p>
<p>
Set the Active-Directory as the resource group, name the virtual machine and set the region. All other settings are left as is.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/93c98d1d-5bfe-48f1-8d2b-20813bd77200" />
</p>
<p>
Set the size to at least 2 cores with 8GB of memory.
</p>
<br />

<p>

</p>
<p>
The image should be Windows 10 Pro version 22H2 x64 Gen2. In the Administrator account section set the username and password. After all the settings are set, review and create.
</p>
<br />

<p>

</p>
<p>
Deployment for the client vm is in progress.
</p>
<br />

<p>

</p>
<p>
Navigate to the dc-1 virtual machine.
</p>
<br />

<p>

</p>
<p>
Locate Network settings.
</p>
<br />

<p>

</p>
<p>
Click on the Network inteface/ IP configuration.
</p>
<br />

<p>

</p>
<p>
Under settings, go to IP configurations, and click on ipconfig1
</p>
<br />

<p>

</p>

<p>
Change the Allocation from Dynamic to Static and save the changes.
</p>
<br />

<p>

</p>
<p>
Notice that tha Private IP Address is set to Static.
</p>
<br />

<p>
  
</p>
<p>
Search for Virtual Machnies.
</p>
<br />

<p>
  
</p>
<p>
Select dc-1 vm.
</p>
<br />
