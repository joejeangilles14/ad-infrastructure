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
Select the Windows 10 Pro version 222 x64 Gen2, set the size to at least 2 cores with 8GB of memory, and if needed set to the correct Zone number.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/270f5945-6048-49df-ab42-40396b9065b1" />
</p>
<p>
In the Administrator account section set the username and password. After all the settings are set, review and create.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3fa4e846-7e67-4420-bca6-2376e0acc652" />
</p>
<p>
Deployment for the client vm is complete.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/b5819d29-76f1-4a7f-a291-3329a6e23a35" />
</p>
<p>
Navigate to the DC-1 virtual machine. Locate Network settings.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/7999150c-34d2-46d1-8ad0-828f8197e78e" />
</p>
<p>
Click on the Network inteface/ IP configuration aka NIC.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/d42a4bbb-3c83-43d7-a140-36e93090725d" />
</p>
<p>
Under settings, go to IP configurations, and click on ipconfig1
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/e361d37e-9fdc-4aa2-99fd-ce327797cd0d" />
</p>
<p>
Change the Allocation from Dynamic to Static and save the changes.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/d6dfd1e5-d4c8-4f69-971d-b06d552c0acd" />
</p>
<p>
Notice that tha Private IP Address is set to Static.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/62ec152e-c695-44c8-a98f-bd6a1e539e83" />
</p>
<p>
Search VM and copy DC-1 IP address.
</p>
<br />

<p>
<img width="1628" height="1172" alt="image" src="https://github.com/user-attachments/assets/42421d1c-e685-46a2-9bc9-331f8e3604db" />
</p>
<p>
Go to Microsoft Remote Desktop and create DC-1 PC by adding the IP address and click Add.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/6d25c0e5-b942-47a2-b093-3e39d36e60fe" />
</p>
<p>
Upon logging into the domain controller successfully, the server manager dashboard should open automatically.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/ee017160-ed33-449f-8e32-bc127993f1a7" />
</p>
<p>
Richt-click on the start icon and go to System.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/279dbf78-c52f-4670-b061-ea1c5a20352b" />
</p>
<p>
In the Windows specifications section, Windows Server 2022 is the correct edition.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/5a0ac7bf-342a-4bd6-a736-86608891b394" />
</p>
<p>
Right-click on the start icon and select Run or press "command + R" to open Run.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c0f1d0be-13dd-41c3-9ca7-9a7fdab4f9a2" />
</p>
<p>
In Run, type wf.msc to open open up Windows Firewall.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c0f1d0be-13dd-41c3-9ca7-9a7fdab4f9a2" />
</p>
<p>
In Run, type wf.msc to open open up Windows Firewall.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/f27a79eb-bdd3-4b44-8dfd-5d1a48c3b79e" />
</p>
<p>
Click on properties and turn the Domain Profile firewall off.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/db7c69a2-91f6-4002-848b-dafa22dd727c" />
</p>
<p>
Turn the Private Profile firewall off.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/cd6e5dde-a497-411b-8b57-cbc3377ea52a" />
</p>
<p>
Turn the Public Profile firewall off.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/7cab6b15-c1f9-47f4-b72d-d175c784c1bd" />
</p>
<p>
Observe that the firewall has been turned off.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/4b9f385d-bdc1-4508-a4ac-1de92f5b67cb" />
</p>
<p>
Click on DC-1 in Azure. scroll to the Networking section and observe the private IP address.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/ad9cdbac-578d-4e10-81a9-37eff487f22c" />
</p>
<p>
Click on the Network/IP configuration.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/587c10c9-c2af-4d57-8d87-83e0194fd1e2" />
</p>
<p>
In the settings tab, go to DNS servers. It shows that the DNS servers is inherited from the virtual network.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/13429a87-727a-447a-94de-d984458b601a" />
</p>
<p>
Click on custom and input DC-1 private IP address, which is 10.0.0.4 then save the changes.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c0c27194-5b6a-45a8-ab2d-2e31fc05afa4" />
</p>
<p>
Go back to virtual machines and select Client-1. CLick on the three dots and restart the virtual machine.
</p>
<br />
