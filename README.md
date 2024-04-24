<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine Windows 10, 4 vCPUs
- Install / Enable IIS in Windows with CGI and Common HTTP Features and IIS Management Console
- From installation files download VC and MySQL
- Install osTicket v1.15.8
- Configure  Roles, Departments, Teams, Agents, Users and 

<h2>Installation Steps</h2>

![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/80d04a51-9aeb-4cb7-b743-7dcf34886282)

<p>
Part 1 (Create Virtual Machine in Azure)
- Create a Resource Group
-Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
-When creating the VM, allow it to create a new Virtual Network (Vnet)
</p>
<br />

![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/afff5cf8-115d-434e-a859-1b011182d7bf)


![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/0512375a-1654-4729-8f59-ea10477105eb)

![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/1c7dab5b-4d5d-46e7-a229-4523a8cd7686)


<p>
Part 2 (Installation)

- Create an Azure Virtual Machine Windows 10, 4 vCPUs

- Open Installation Files and Install / Enable IIS in Windows WITH CGI and Common HTTP Features, World Wide Web Services -> Application Development Features ->
[X] CGI, [X] Common HTTP Features, AND IIS Management Console, Internet Information Services -> Web Management Tools -> IIS Management Console, [X] IIS Management Console

- From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

- From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

- Create the directory C:\PHP

- From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

- From the Installation Files, download and install VC_redist.x86.exe.

- From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->

- Open IIS as an Admin

- Register PHP from within IIS

- Reload IIS (Open IIS, Stop and Start the server)

- Install osTicket v1.15.8 and Download osTicket from the Installation Files Folder, Extract and copy “upload” folder to c:\inetpub\wwwroot, Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

-Reload IIS (Open IIS, Stop and Start the server)

- Go to sites -> Default -> osTicket, On the right, click “Browse *:80”

- Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager, Click “Enable or disable an extension”, Enable: php_imap.dll, Enable: php_intl.dll, Enable: php_opcache.dll, Refresh the osTicket site in your browse, observe the changes

- Rename: ost-config.php, From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

- Assign Permissions: ost-config.php, Disable inheritance -> Remove All, New Permissions -> Everyone -> All

-Continue Setting up osTicket in the browser (click Continue), Name Helpdesk, Default email (receives email from customers)

- From the Installation Files, download and install HeidiSQL., Open Heidi SQL, Create a new session, root/*****, Connect to the session, Create a database called “osTicket”

- Continue Setting up osticket in the browser, MySQL Database: osTicket, MySQL Username: root, MySQL Password: Password1, Click “Install Now!”

- Browse to your help desk login page: http://localhost/osTicket/scp/login.php

- End Users osTicket URL: http://localhost/osTicket/ 

- Clean up, Delete: C:\inetpub\wwwroot\osTicket\setup, Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Notes: Browse to help desk login page: http://localhost/osTicket/scp/login.php , End Users osTicket URL: http://localhost/osTicket/ 
</p>
<br />

![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/187b6623-ea6a-4855-9676-2dcd538dd1ba)

![image](https://github.com/QuintiaLyman/osticket-prereqs/assets/84552471/011c1519-131f-4994-a8d3-21659383e3a4)


<p>
Part 3 (Post Installation Setup)
- Configure Roles
Admin Panel -> Agents -> Roles Supreme Admin
  
- Configure Departments, Admin Panel -> Agents -> Departments
  
- System Administrators, Configure Teams, Admin Panel -> Agents -> Teams
  
- Level I Support, Level II Support, Allow anyone to create tickets
  
-Admin Panel -> Settings -> User Settings, Registration Required: Require registration and login to create tickets 

- Configure Agents (workers), Admin Panel -> Agents -> Add New, Jane, John
  
- Configure Users (customers), Agent Panel -> Users -> Add New, Karen ,Ken
  
- Configure SLA, Admin Panel -> Manage -> SLA, Sev-A (1 hour, 24/7), Sev-B (4 hours, 24/7), Sev-C (8 hours, business hours)
  
- Configure Help Topics, Admin Panel -> Manage -> Help Topics, Business Critical Outage, Personal Computer Issues, Equipment Request, Password Reset

Part 4 (Tickets and Ticket Lifecycle)
Just practice creating, triaging, and solving tickets. I recommend watching the video to learn about triaging multiple tickets.

Ticket examples:
Sev-A (1 hour, 24/7) [entire mobile/online banking system is down] -> SysAdmins
Sev-B (4 hours, 24/7) [accounting department needs adobe upgrade, broken]
Sev-B/C (2 hours, business hours) [CFO’s laptop seems a bit slow]
</p>
<br />
