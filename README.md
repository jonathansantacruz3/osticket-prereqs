<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Windows 10 virtual machine
- Install & enable Internet Information Services with CGI, Common HTTP Features, and IIS Management Console  
- Download & install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Download & install the Rewrite Module (rewrite_amd64_en-US.msi)
- Create the directory C:\PHP
- Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
- Download & install VC_redist.x86.exe
- Download & install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
- Install osTicket v1.15.8
- Download and install HeidiSQL

<h2>Installation Steps</h2>

Step 1: Create Virtual Machine in Azure 

To start off, in my Azure subscription, I created a resource group to help organize my resources. I named my resource group "RG-osTicket". The creation of a virtual machine resource can be located by simply typing in the search bar "virtual machine", and then clicking on the icon to begin the process. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/2a0658d0-1516-447c-a322-6096949723fa)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/36f38d64-d951-439e-9bc1-82f6d0c82bf3)

I selected my subscription and the resource group "RG-osTicket" that i created in the drop down menu for the corresponding fields. I proceeded to assign the name "vm-osticket" to my virtual machine, utilizing lowercase letters. It wouldn't validate my machine if i utilized capital letters. When it comes to choosing a region for a resource, it is best practice to appoint the region closest to yourself or whoever will be working with those resources. I am in the west part of the USA so i chose "(US) West US 3. This is basically where the data center will house that particular resource. For the image i used a Windows 10 Pro, version 21H2, with 4 virtual CPUs totaling 16 GB of memory. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/b88c3640-854d-4ec9-907d-1e5a528514a4)

For the administrator credentials i used "labuser" as my user name and Password1 as my password to simplify the process. I enabled port 3389 to allow remote desktop access. I then marked the licensing box to signify i confirm. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/c8dc069c-bb7c-4408-b3bd-a8a10e543db9)

In the tabs below i navigated to networking and confirmed Azure created the necessary virtual network, subnet, public IP address, and a basic NIC network security group. I then clicked on the blue "Review + Create" button. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/27ed290a-5149-4601-8cc4-33a9a2fcacd5)

Once validated it took me to this screen and i knew it passed because of the green checkmark and the notification confirming it. 


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
