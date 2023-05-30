<p align="center">
<img src="https://i.imgur.com/r7UlOH2.png" alt="osTicket logo"/>
</p>

<h1>Step-by-Step Guide: Creating a Virtual Machine in Azure and Setting Up osTicket</h1>
This tutorial outlines the prerequisites and installation process for osTicket, an open-source help desk ticketing system. It covers the setup of a Virtual Machine in Azure, enabling Internet Information Services (IIS), installation of PHP and additional components, configuration of osTicket, and the setup of the MySQL database.<br />
<h2>Environments and Technologies Used</h2>
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
<h2>Operating Systems Used </h2>
- Windows 10 (21H2)
<h2>Prerequisites:</h2>
Azure account: You should have an active Azure account to provision a Virtual Machine and create a new Virtual Network (Vnet) in Azure.<br>

Access to a Windows 10 Virtual Machine: Ensure that you have access to a Windows 10 Virtual Machine in Azure for setting up osTicket.<br>

Remote connection software: Install a remote connection software such as Remote Desktop Protocol (RDP) client to establish a remote connection to the Azure Virtual Machine.<br>

Administrator access: Make sure you have administrative access to the Azure Virtual Machine to perform the necessary configurations and installations.<br>

Internet Information Services (IIS): Familiarize yourself with the process of enabling and configuring Internet Information Services (IIS) on a Windows machine.<br>

Downloaded files: Prior to starting the guide, download the following files to your local machine:<br>

PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)<br>
Rewrite Module (rewrite_amd64_en-US.msi)<br>
PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)<br>
VC_redist.x86.exe<br>
MySQL 5.5.62 (mysql-5.5.62-win32.msi)<br>
HeidiSQL: Download and install HeidiSQL, a MySQL database management tool, on your local machine.<br>

Basic knowledge of PHP and MySQL: Familiarity with PHP and MySQL concepts will be beneficial for configuring and setting up osTicket.<br>
<h2>Installation Steps</h2>

  <h2>Step 1: Provision a Virtual Machine in Azure</h2>
  <p>Provision a Virtual Machine in Azure with a Windows 10 operating system, 2-4 Virtual CPUs, and a new Virtual Network (Vnet). Establish a remote connection to the Virtual Machine.</p>

  <p>
  <img src="https://i.imgur.com/3wkonsP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 2: Configure Internet Information Services (IIS)</h2>
  <p>
    a. Navigate to Control Panel -> Programs -> Turn Windows Features On or Off.<br>
    b. Select "Internet Information Services," expand the options for IIS, World Wide Web Services, and Application Development Features.<br>
    c. Enable Common HTTP Features and CGI. Click OK.<br>
    d. Verify the functionality of IIS by entering "127.0.0.1" in the search bar.
  </p>

  <p>
  <img src="https://i.imgur.com/TzY5klG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 3: Install additional components for osTicket</h2>
  <p>
    a. Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).<br>
    b. Download and install the Rewrite Module (rewrite_amd64_en-US.msi).<br>
    c. Create the directory C:\PHP.<br>
    d. Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and extract its contents into the C:\PHP directory.<br>
    e. Download and install VC_redist.x86.exe (required for PHP).<br>
    f. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) with the Standard Configuration, setting the password as "Password1."
  </p>
  
  <h2>Step 4: Configure PHP with IIS</h2>
  <p>
    a. Open IIS Manager as an administrator and launch PHP Manager.<br>
    b. Register a new PHP version by browsing to php-cgi.exe (located within the PHP installation).<br>
    c. Restart IIS within IIS Manager app.
  </p>

  <p>
  <img src="https://i.imgur.com/6n4nCAt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 5: Install osTicket v1.15.8</h2>
  <p>
    a. Download osTicket and extract its contents.<br>
    b. Rename the "upload" folder to "osTicket" and move it to C:\inetpub\wwwroot.<br>
    c. Stop and start the IIS server to reload the configuration.<br>
    d. Access the osTicket site by navigating to sites -> Default -> osTicket and clicking "Browse *:80" on the right.
  </p>

  <p>
  <img src="https://i.imgur.com/wF9KLI4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 6: Enable the required PHP extensions</h2>
  <p>
    a. In IIS, navigate to sites -> Default -> osTicket.<br>
    b. Open PHP Manager, double-click on "Enable or disable an extension."<br>
    c. Enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.<br>
    d. Refresh the osTicket site in your browser to observe the changes.
  </p>

  <p>
  <img src="https://i.imgur.com/HVujQKF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 7: Rename and configure ost-config.php</h2>
  <p>
    a. Rename ost-sampleconfig.php (located in C:\inetpub\wwwroot\osTicket\include) to ost-config.php.<br>
    b. Adjust the permissions for ost-config.php by accessing its properties -> security -> advanced -> disabling inheritance -> removing all permissions.<br>
    c. Add a new principal named "Everyone" with "Full control" permissions. Click OK and apply the changes.
  </p>

  <p>
  <img src="https://i.imgur.com/Pz98age.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 8: Complete the osTicket setup in the browser</h2>
  <p>
    a. Click "Continue" on the osTicket site.<br>
    b. Provide a name for your help desk and specify the default email address for receiving customer emails.<br>
    c. Fill in all the necessary details until you reach the database settings.
  </p>
  
  <h2>Step 9: Set up the MySQL database using HeidiSQL</h2>
  <p>
    a. Download and install HeidiSQL.<br>
    b. Open HeidiSQL and create a new session using "root" as the username and "Password1" as the password.<br>
    c. Open the session and create a database called "osTicket."
  </p>

  <p>
  <img src="https://i.imgur.com/UJYHkPz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  
  <h2>Step 10: Proceed with the osTicket setup in the browser</h2>
  <p>
    a. Provide "osTicket" as the MySQL Database and "root" as the MySQL Username. <br>
    b. Press "Install Now!" <br>
    c. Afterwards: Delete the C:\inetpub\wwwroot\osTicket\setup folder. <br>
    d. Set the permissions of C:\inetpub\wwwroot\osTicket\include\ost-config and leave it so they can only read and execute + read
  </p>
  
</body>
</html>

