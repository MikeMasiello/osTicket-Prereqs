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

<img src="https://i.imgur.com/UsQEt9Y.png" height="50%" width="50%" alt="register PHP "/>
</p>
8. Once you have downloaded and extracted the zip file ino the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.
</p>
9. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->

Make the new root password: Password1

<img src="https://i.imgur.com/7VzSMlx.png" height="50%" width="50%" alt="register PHP "/>
<img src="https://i.imgur.com/82phKla.png" height="50%" width="50%" alt="register PHP "/>
</p>
10. Now that the files are downloaded and installed search for IIS in the windows search bar. Open IIS as an administrator. The program should look like this.
<img src="https://i.imgur.com/3MrxnWG.png" height="50%" width="50%" alt="register PHP "/>

11. Register PHP from within IIS. Click on PHP Manager

<img src="https://i.imgur.com/QFEpNQY.png" height="50%" width="50%" alt="register PHP "/>

Register new PHP version.

<img src="https://i.imgur.com/AfmdyE9.png" height="50%" width="50%" alt="register PHP "/>

Provide a path to the php executable file (php-cgi.exe)). Go to C Drive -> PHP -> click on php-cgi file.

<img src="https://i.imgur.com/pT4jVrH.png" height="50%" width="50%" alt="register PHP "/>

Reload IIS (Open IIS, Stop and Start the server)

<img src="https://i.imgur.com/PvJvWQe.png" height="50%" width="50%" alt="register PHP "/>

</p>
<p>
12. Install osTicket v1.15.8
Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”


Reload IIS 
(Open IIS, Stop and Start the server)


13. Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

<img src="https://i.imgur.com/jcKTKPB.png" height="50%" width="50%" alt="register PHP "/>
<p>
	
Note that some extensions are not enabled.
	
<img src="https://i.imgur.com/eou98O6.png" height="50%" width="50%" alt="register PHP "/>
<p>
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
<p>	
<img src="https://i.imgur.com/zUrdij2.png" height="50%" width="50%" alt="register PHP "/>


Click “Enable or disable an extension”
<p>
<img src="https://i.imgur.com/PxeTVhY.png" height="50%" width="50%" alt="register PHP "/>

Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll

<img src="https://i.imgur.com/jqXym3Q.png" height="50%" width="50%" alt="register PHP "/>

14. Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder. Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

We are going to rename the ost-sampleconfig.php to ost-config.php
Refresh the osTicket site in your browse, observe the changes
Now that we have renamed the files, right click on the file and go to properties. From there click security, click on advance, and disable the inheritance. We will select Remove all inherited permissions from this object.

Now we will add new permissions.
Click Add

<img src="https://i.imgur.com/0XLmGXd.png" height="50%" width="50%" alt="Configure Permissions Install OS Ticket "/>
</p>
<p>
Select Principal
<p>	
<img src="https://i.imgur.com/hleshE5.png" height="50%" width="50%" alt="Configure Permissions Install OS Ticket "/>
	
Type "Everyone" in the box
	
<img src="https://i.imgur.com/JQUfl2j.png" height="50%" width="50%" alt="Configure Permissions Install OS Ticket "/>
Check "Full Control" and all other boxes. 
<img src="https://i.imgur.com/sxIQRff.png" height="50%" width="50%" alt="Configure Permissions Install OS Ticket "/>

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
