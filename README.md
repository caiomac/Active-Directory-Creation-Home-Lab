<h1>Active Directory Creation</h1>

<h2>Description</h2>
This project sets up a virtual environment using Oracle VM VirtualBox with Windows 10 and Windows Server. Network configurations enable communication via IP addresses and NAT Networks.. Windows machine joins an Active Directory domain with Remote Desktop enabled. PowerShell scripting automates the task for account creation.
<br/>
<br/>
<i>Estimated completion time: 2-3 hours</i>
<br/>
<br/>
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/b870df29-5e88-4e53-a8d5-6f7e703a970a" width="700">
</div>
<br />

<h2>Objectives</h2>
The objective of the lab is to provide a hands-on learning experience in setting up a virtualized environment simulating a real company environment. By creating and configuring virtual machines (VMs) including Windows 10 and Windows Server, the lab aims to teach skills such as network configuration and virtualization. Joining Windows machines to an Active Directory domain and using the created accounts to log into these machines also adds to the learning objectives. PowerShell scripting was used for automating the task of creating 1000 user accounts.

<h2>Skills learned</h2>

- Setting up VMs (Windows 10 and Windows Server) in Oracle VM VirtualBox. <br />
- Configuring IP addresses, NAT Networks for VMs. <br />
- Troubleshooting network connectivity (ping, DNS settings). <br />
- Joining Windows machines to a domain. <br />
- PowerShell scripting for account creation (Get-Content, ConvertTo, New-ADOrganizationalUnit, Write-Host, New-AdUser -Account Password). <br />


<h2>Tools Used </h2>

- Oracle VM VirtualBox Manager: For creating and managing virtual machines (VMs).<br />
- PowerShell: For scripting and automation tasks.<br />
- Windows Server 2022: Operating system used for Active Directory Domain Services setup.<br />
- Microsoft Windows 10: Operating system for target machine in the lab.<br />


<h2>Program walk-through:</h2>

<h3>Step 1 - VM Installation</h3> 
<b><i>1. Installing Oracle VM VirtualBox Manager</b></i>
<br /> 
  Navigated to https://www.virtualbox.org/, downloaded the compatible version, and installed it with dependencies.
<br/> 
<br/> 
<b><i>2. Installing Windows Server 2019</b></i>
<br /> 
  Visited https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019, and clicked 64bit edition in English. In Oracle VM VirtualBox Manager, clicked "Add" to create a new VM, named it, chose the previously downloaded Windows Server 2019 ISO, select 8000MB RAM, 1 CPU, 50GB virtual disk, and finish. Started the VM, followed the installation prompts, selected "Custom: Install Windows only (advanced)", and let Windows Server install.
<br />
<br />
<b><i>3. Installing Windows 10</b></i>
<br /> 
  Visited https://www.microsoft.com/en-ca/software-download/windows10, got "Create Windows 10 installation media", clicked "Download tool now", chose "Create installation media (USB flash drive, DVD, or ISO file) for another PC", then selected "ISO file" and saved it. In Oracle VM VirtualBox Manager, clicked "Add" to create a new VM, named it, chose the previously downloaded Windows 10 ISO, selected 800MB RAM, 1 CPU, 50GB virtual disk, and finish. Started the VM, followed the installation prompts, selected "Custom: Install Windows only (advanced)", and let Windows 10 install.
<br />
<br />
<h3>Step 2 - Setting up the Domain Controller:</h3>  
<b><i>1. Setting up IP addresses on the Windows Server</b></i>
<br/>
  Setting up internal and internet IPs on a Windows Server enables secure, segmented network communication. Internal IPs manage local resource access, while internet IPs allow external connectivity. This dual-IP setup enhances security, traffic control, and network performance by isolating internal resources from external exposure.
<br/>
<br/> 
  The domain controller has 2 network connections, one is the internet and the other responsible for internal network. First step was renaming them accordingly and then assigning the right addresses to the internal network adapter:
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/0a5219e3-83a4-44ae-8b68-8682d0e65fb0" width="500">
</div>
<br/> 
<br/> 
<b><i>2. Setup Active Directory Domain Services on the Windows Server</b></i>
<br /> 
  Setting up Active Directory Domain Services (AD DS) on a Windows Server creates a centralized framework for managing users, devices, and resources within a network. It provides authentication, authorization, and policy enforcement, enabling secure, organized access control. With AD DS, administrators can streamline network management and improve security through centralized policies and user data.
<br />
<br />
  On the Windows server, I opened up Server Manager. Navigated to Manage > Add Roles and Features. Selected Next > Next, and checked Active Directory Domain Services > Add Features. 
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/b935f642-802e-431c-86fa-00a1c6a4dadb" width="500">
</div>
<br />
  Advanced until I could select install.
<br />
  After it was completely deployed, the server then was a domain and Active Directory Users and Computers was set.
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/155c1eed-c5a2-4db5-a89b-809003c35cc0" width="500">
</div>
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/3b5391c5-cb2c-422f-a7c1-ac1748ec970b" width="700">
</div>
<br />
<br />
<b><i>3. Admin account creation</b></i>
<br /> 
  Creating an admin account in Active Directory grants a user elevated permissions to manage and configure the network's resources. 
<br />
<br />
First, an admin organization unit called _ADMINS was created and an admin was created on it (a-cmacedo) by using the domain admins membership.
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/f4eadc73-668a-454d-94c1-11f364731183" width="700">
</div>
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/6fd63e7c-b947-4be5-b33c-772e98eff742" width="350">
</div>
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/7f61e518-caef-44f3-9fc8-292245ee44d1" width="350">
</div>
<br />
Account was then usable.
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/8f3bbcdc-f460-4ca1-aeb5-f231a52a5ffe" width="500">
</div>
<br />
<b><i>3. Admin account creation</b></i>
<br />
Setting up Routing and Remote Access Service (RAS) with Network Address Translation (NAT) on a Windows Server enables secure remote access and internet sharing within a network. RAS allows users to connect remotely, while NAT translates internal IPs to a single public IP, protecting internal resources from direct exposure. This configuration is essential for supporting remote connectivity and safeguarding network traffic.
<br />
<br />
On the Windows server, I opened up Server Manager again. Navigated to Manage > Add Roles and Features. Selected Next > Next, and checked Remote Access > Next.
<br />
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/e1afbda8-7a3b-4583-8696-fdd822642046" width="500">
</div>
<br />
It was clicked next some times, and in Role Services, DirectAccess and VPN(RAS) and Routing was selected > Next.
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/a5b86795-38e6-48e8-8ccc-6079b31e4de0" width="500">
</div>
<br />
After finishing installation, in Server Manager, it was clicked in Tools > Routing  and Remote access > Right clicked DC > Enable and configure routing and remote access:
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/838ab384-3c6f-44e2-8c7d-3f819cdc677a" width="500">
</div>
<br />
<br />
And then selected the network adapter with internet access:
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/691b8774-c3e9-427a-8618-fa1c628aa83a" width="700">
</div>
<br />
So RAS/NAT was configured as shown next:
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/9e22e633-265c-4ee3-ac29-c53f74c8a8f8" width="500">
</div>
<br />
<br />
<b><i>4. DHCP Setup</b></i>
<br />
Setting up DHCP (Dynamic Host Configuration Protocol) on a Windows Server automates the assignment of IP addresses to devices within a network. This service simplifies network management by dynamically allocating IPs, reducing manual configuration, and preventing address conflicts. DHCP ensures efficient, centralized IP management, improving network organization and connectivity.
<br />
On the Windows server, I opened up Server Manager again. Navigated to Manage > Add Roles and Features. Selected Next > Next, and checked DHCP Server > Next.
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/454a1988-e8ac-4525-a46b-8c24b5a4c0e6" width="500">
</div>
<br />
Then it was clicked in tools > DHCP, and set the IP range from 172.16.0.100 to 172.16.0.200 with the subnet mask 255.255.255.0
<br/> 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/5ff794dc-196d-4ec8-9139-1d6a31400ab0" width="500">
</div>
<br />
Next it was set the Lease duration, in other words how long it would take for the IP to be reset and available again for new devices and then the server IP was set as router.
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/81382a6f-f493-4d89-9fe9-9e07d88fce49" width="600">
</div>
<br />
So, DHCP was Authorized and IPv4 was refreshed for it to work
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/78fd58e9-bb63-4fc5-aa30-af29c2d14a5d" width="700">
</div>
<br />
Last thing, it’s necessary to configure Server Options by enabling Router option, and adding the server ip as server name.
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/bc4d45d2-a30f-47a9-8b0f-2b10d78ed4a0" width="400">
</div>
<br />
<h3>Step 3 - Creating 1000+ users through a PowerShell script</h3>
Creating users in Active Directory via PowerShell automates bulk provisioning, saving time and reducing errors. This method ensures efficient and consistent user setup across large environments.
<br />
<br />
It was opened PowerShell ISE as admin and set execution policy to unrestricted to create the script below: 
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/444631b9-606b-49dd-b0cf-f6b4ebbc3396" width="700">
</div>
<br />
In the next pictures we see the before and after the script was ran:
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/44eb165a-b626-4606-b8d0-4f7f0aaa31ed" width="700">
</div>
<br />
<h3>Step 4 - Starting the client computer in the domain</h3>
Once everything is set now, if it’s tried to start the client computer as set of internal network, it’ll be in the domain as shown below. 
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/c1b9a439-221d-41b0-b54b-f4ef9d0d1287" width="700">
</div>
<br />
And the workstation will be connected to the internet through the domain.
<br />
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/a1df5100-283c-4c14-b55f-bf1402ad07ce" width="500">
</div>
<br />
For better management computer was renamed to WindowsPC and is already visible in DHCP and Active Directory (172.16.0.100 was another testing machine) 
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/88d990b3-bc49-49e6-b2b6-add3def34d04" width="700">
</div>
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/d4c4de0a-e69a-4fcb-9ef3-1d025aac1a39" width="500">
</div>
<br />
Once the computer is in AD, it’s possible to login to it by using one of the user accounts created.
<br />
<br/> 
<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/be015f49-c14b-4b69-b7f9-b0549e29a876" width="400">
</div>
<h2>Summary</h2>
I had reached the end of the walk-through! With the conclusion of the last part of this step-by-step walk-through, I had a successful setup and communication between 2 Virtual Machines: Windows 10 and Windows Servers. I should also be able to automatically connect a computer to the domain once it’s in the same network as the server and sign in by using any of the accounts from the Active Directory.


  <!--
 ```diff
