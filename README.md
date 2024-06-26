# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This walkthrough outlines the prerequisites and installation of the open-source help desk ticketing system OS Ticket. Installation will allow you to move onto learning how to configure OS Ticket post installation and move onto the lifecycle of a ticket from intake to resolution within the open-source help desk ticketing system osTicket..<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Interet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2> 
1. Create a virtual machine using the Azure Portal, https://portal.azure.com/.  Setup your virtual machine with Windows 10 Pro, version 22H2.  Create a virtual machine with at least 2 vcpus and 16 GBS of 
   memory.
</p>
2. After the virtual machine is created, connect to it by using the public IP address the vm is setup with.  Use your Remote Desktop app to connect to the VM. 
</p>



	

<img src="https://i.imgur.com/WJxTlmA.png" height="50%" width="50%" alt="OS Ticket VM Creation"/>
</p>

<img src="https://i.imgur.com/2icN8RH.png" height="50%" width="50%" alt="OS Ticket VM Creation"/>

3. Once you have connected to your virtual machine, go to control panel.  From control panel open up programs. Select, Turn Windows features on and off.
<img src="https://i.imgur.com/71kXs7z.png" height="50%" width="50%" alt="Control Panel"/>
<img src="https://i.imgur.com/r02LyEz.png" height="50%" width="50%" alt="Control Panel"/>  


  
4. Install/enable IIS in Windows with CGI and Common HTTP Features
   * World Wide Web Services-> Application Development Features-> [X] CGI [x] Common HTTP Features
   * NOTE: Make sure all Common HTTP Features ae checked. 
<img src="https://i.imgur.com/6iKiZcW.png" height="50%" width="50%" alt="Install IIS features"/>
    
</p>
To verify that IIS is installed/enabled go to a browser of your choice and search for 127.0.0.1, it should look something like this. 
<img src="https://i.imgur.com/0DCZvHu.png" height="50%" width="50%" alt="Install IIS"/>
  

</p>
<br />

5. Now that IIS is enabled, from the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

6. From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

7. Create a folder in the C drive called PHP, directory C:\PHP
From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
</p>
<br />
8. Once you have downloaded and extracted the zip file ino the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe. 

<img src="https://i.imgur.com/3MrxnWG.png" height="80%" width="80%" alt="register PHP "/>

Open IIS as an Admin

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)


<img src="https://i.imgur.com/ntv2wQp.png" height="80%" width="80%" alt="Configure Permissions Install OS Ticket "/>
</p>
<p>
Install osTicket v1.15.8
Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”


Reload IIS 
(Open IIS, Stop and Start the server)
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

<img src="https://i.imgur.com/BWU2e2k.png" height="80%" width="80%" alt="Configure Permissions Install OS Ticket "/>
</p>
<p>
<img src="https://i.imgur.com/kgipxsi.png" height="80%" width="80%" alt="Configure Permissions Install OS Ticket "/>

	
Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

<img src="https://i.imgur.com/goQq97z.png" height="80%" width="80%" alt="Configure Permissions Install OS Ticket "/>
</p>
<p>

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

<img src="https://i.imgur.com/SSsZNjJ.png" height="80%" width="80%" alt="Install Heidi SQL "/>

<img src="https://i.imgur.com/27mNbmT.png" height="80%" width="80%" alt="Install Heidi SQL "/>

From the Installation Files, download and install HeidiSQL, mOpen Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”
</p>
<p>
<img src="https://i.imgur.com/u5rZPl8.png" height="80%" width="80%" alt="Install OSTicket "/>
</p>
<p>
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”
</p>
<p>
<img src="https://i.imgur.com/IeDmuTt.png" height="80%" width="80%" alt="Install OSTicket cleanup "/>
</p>
<p>	
Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<p>
<img src="https://i.imgur.com/5gT24ve.png" height="80%" width="80%" alt="Install OSTicket Completed "/>	
</p>
<p>
<h2>OS Ticket Installation Complete!
