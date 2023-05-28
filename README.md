<!DOCTYPE html>
<html>
<head>
  <title>osTicket - Prerequisites and Installation</title>
</head>
<body>
  <p align="center">
    <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
  </p>

  <h1>osTicket - Prerequisites and Installation</h1>
  <p>
    This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.
  </p>

  <h2>Environments and Technologies Used</h2>
  <ul>
    <li>Microsoft Azure (Virtual Machines/Compute)</li>
    <li>Remote Desktop</li>
    <li>Internet Information Services (IIS)</li>
  </ul>

  <h2>Operating Systems Used</h2>
  <ul>
    <li>Windows 10 (21H2)</li>
  </ul>

  <h2>List of Prerequisites</h2>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
    <li>Item 5</li>
  </ul>

  <h2>Installation Steps</h2>
  <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  <p>
    Step 1: Enable Internet Information Services (IIS): 
    Go to Control Panel -> Programs -> Turn Windows Features On or Off -> Check Internet Information Services. Expand IIS, expand World Wide Web Services, and expand Application Development Features. Make sure to check Common HTTP Features and CGI. Press OK. To check if IIS is working, type "127.0.0.1" in the search bar, and a page should come up. If not, uncheck IIS and reinstall it in Control Panel.
  </p>
  <br />

  <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  <p>
    Step 2: Download and install additional components for osTicket:
    <ul>
      <li>Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).</li>
      <li>Download and install the Rewrite Module (rewrite_amd64_en-US.msi).</li>
      <li>Create the directory C:\PHP.</li>
      <li>Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and extract it into the PHP directory.</li>
      <li>Download and install VC_redist.x86.exe (needed for PHP).</li>
      <li>Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) using the Standard Configuration and set the password as "Password1."</li>
    </ul>
  </p>
  <br />

  <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  <p>
    Step 3: Register PHP with IIS:
    Open IIS as an admin, open PHP Manager, click on "Register New PHP Version," and navigate to C:\PHP\php-cgi.exe. Select the version and click "Change PHP Version." If PHP Manager doesn't open, uninstall PHP Manager and reinstall it using Web Platform Installer.
  </p>
  <br />

  <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  <p>
    Step 4: Configure PHP:
    Open C:\PHP\php.ini in a text editor, find "extension_dir," and set it as "extension_dir = "C:\PHP\ext"." Find "upload_max_filesize" and set it as "upload_max_filesize = 10M." Find "max_execution_time" and set it as "max_execution_time = 300." Save the changes and close the file.
  </p>
  <br />

  <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  </p>
  <p>
    Step 5: Configure IIS:
    Open IIS, select the Default Web Site, and click on "URL Rewrite." Import the provided osTicket web.config file. Restart IIS.
  </p>
  <br />
</body>
</html>
