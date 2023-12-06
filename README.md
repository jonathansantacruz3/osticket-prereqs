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

<h3>Step 1: Create Virtual Machine in Azure</h3>

To start off, in my Azure subscription, I created a resource group to help organize my resources. I named my resource group "RG-osTicket". The creation of a virtual machine resource can be located by simply typing in the search bar "virtual machine", and then clicking on the icon to begin the process. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/2a0658d0-1516-447c-a322-6096949723fa)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/36f38d64-d951-439e-9bc1-82f6d0c82bf3)

I selected my subscription and the resource group "RG-osTicket" that I created in the drop down menu for the corresponding fields. I proceeded to assign the name "vm-osticket" to my virtual machine, utilizing lowercase letters. It wouldn't validate my machine if I utilized capital letters. When it comes to choosing a region for a resource, it is best practice to appoint the region closest to yourself or whoever will be working with those resources. I am in the west part of the USA so i chose "(US) West US 3. This is basically where the data center will house that particular resource. For the image i used a Windows 10 Pro, version 21H2, with 4 virtual CPUs totaling 16 GB of memory. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/b88c3640-854d-4ec9-907d-1e5a528514a4)

For the administrator credentials I used "labuser" as my user name and Password1 as my password to simplify the process. I enabled port 3389 to allow remote desktop access. I then marked the licensing box to signify I confirm. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/c8dc069c-bb7c-4408-b3bd-a8a10e543db9)

In the tabs below I navigated to networking and verified Azure created the necessary virtual network, subnet, public IP address, and a basic NIC network security group. I then clicked on the blue "Review + Create" button. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/27ed290a-5149-4601-8cc4-33a9a2fcacd5)

<p>Once validated it took me to this screen and I knew it passed because of the green checkmark and the notification reaffirming it.</p>

In order to get the VM's IP address I searched for virtual machines in Azure and clicked on the newly created VM. Under networking, the address is available to copy to the computer's clipboard. 
In Window's search bar I typed "remote desktop" and pasted the IP address. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/b552e099-bb1e-4834-afff-0245ad53104d)

After the connection is made, I used the labuser credentials I designated when creating the VM. 

<h3>Step 2: Installation of prerequisites for osTicket</h3>
<p>The prereqs used for the installation were stored on my google drive for offline use. First I installed and enabled was Internet Information Services or IIS along with CGI, common HTTP features, and IIS Management Console. IIS and it's components installed allowed the machine to function as a web server to permit osTicket to run as a website.</p>

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/dc62a2cc-bb31-4244-bd63-b430ba7272e9)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/eeacf1fb-d9b1-435c-9579-b66506721b00) 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/cef4aa5f-45e6-47e7-8c09-26248b577b86)

Expand Common HTTP features > check all boxes > OK 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/05124a30-ce22-43a7-8956-8a5f76689c06)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/9793e29b-fa66-4064-9dbd-036616fafb1c)

Verified web server was installed by opening up a browser and typed the IP address 127.0.0.1 (loopback address that the machine uses to communicate to itself) in the  URL. I knew it was working when the browser displayed the image below.  

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/17dfe4ba-82e7-415e-a8c6-adb1a4eb0705)

Downloaded and installed PHP manager for IIS. This tool is used to install and manage PHP extensions on IIS. It also helps to register, configure, run, check and troubleshoot PHP versions on the same server. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/bc193501-e51f-472a-8b64-96ed0a245a15)

Downloaded & installed the rewrite module program. This is utilized with osTicket to grant friendly URLs for the web-based support ticket system. Friendly URLs are more readable, memorable, and SEO-friendly than the default URLs. For example, a friendly URL can look like this 

https://example.com/ticket/1234

vs.

https://example.com/ticket.php?id=1234<br />



After I installed the rewrite module I created a new directory in the C drive called C:\PHP to store the PHP download data. 
The next step was downloading PHP and unzipping it into the new directory.

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/54c38819-26c2-4690-8a59-ddccdd2253eb)


Following the prior install I downloaded and installed VC_redist_x86.exe. This is a standard distributable package shared code that enabled me to run PHP on my PC. 

Once this was installed in moved on to downloading and installing MySQL server. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/1a1cf48b-e447-427c-be13-e1b07f9350a7)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/f293073f-f1a5-425f-9b6c-ef29dfceebda)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/2e5f8139-99b3-48e1-9ed5-a10c194bc1d0)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/cf9cec00-73be-4047-8633-706db9024a04)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/93117473-cd14-465c-882c-a3504feaa0ac)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/412a0d5c-bfda-4918-9b10-a4363d4e8cb5)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/d26fa8a1-512a-4f40-b3f6-210fc13f8ffe)

After completion, I opened IIS as an administrator to register PHP.

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/4d96bcf1-2092-4c54-a3c7-bf34357a2645)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/02745542-4c96-428f-ad2e-a0ddd1301380)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/cd2895eb-43b4-48c0-b64d-f0e6764ad2df)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/b4d57603-2311-4afe-9589-4b1836d11338)

Once registered, I refreshed the server to reflect the changes. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/a8e59850-32c0-4a3c-875a-4f9dc14f2b3b)

Then I followed with the download and install of osTicket from my google drive. I opened my downloads folder in my WIndows machine and extracted the "upload folder" located within the osTicket zipped file and copied it to: 

C:\inetpub\wwwroot

Once copied, locate the folder, rename it "osTicket", and refresh the IIS server by clicking restart in the IIS manager. Afterwards, I clicked on "sites" on the left side of the manager pane and from the drop down options "Default Web Site" was visible. Within this folder, there was the "osTicket" folder. "Browse *:80(http)" appeared on the right side of the manager pane and i clicked it to verify osTicket showed up in the broswer. 

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/42b6fb57-29b7-4dea-9f07-6192c1675d74)

![image](https://github.com/jonathansantacruz3/osticket-prereqs/assets/151465848/0033ec21-a8dd-4ac5-bb58-f272e4fe869b)


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
