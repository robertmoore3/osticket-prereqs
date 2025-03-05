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
- A suitable Azure subscription

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Download Required Files</h2>
<p>
1. Download osTicket-Installation-Files.zip
2. Extract it to your Desktop—it will create a folder named osTicket-Installation-Files.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Install IIS with CGI</h2>
<p>
1. Open Windows Features (Control Panel > Programs > Turn Windows features on or off).
2. Enable Internet Information Services (IIS).
3. Expand World Wide Web Services > Application Development Features.
4. Check ✅ CGI.
5. Click OK and restart the VM if needed.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Install Required Components</h2>
<h3>Install PHP Manager for IIS</h3>
<p>
1. Open the osTicket-Installation-Files folder.
2. Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).
</p>
<h3>Install IIS Rewrite Module</h3>
<p>
1. Install Rewrite Module (rewrite_amd64_en-US.msi).
</p>
<h3>Install PHP</h3>
<p>
1. Create a new folder: C:\PHP.
2. Extract PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into C:\PHP.
</p>
<h3>Install Visual C++ Redistributable</h3>
<p>
1. Install VC_redist.x86.exe from the osTicket-Installation-Files folder.
</p>
<h3>Install MySQL 5.5.62</h3>
<p>
1. Install MySQL 5.5.62 (mysql-5.5.62-win32.msi).
2. Choose Typical Setup during installation.
3. After installation, launch the MySQL Configuration Wizard:
    -Select Standard Configuration.
    -Set the MySQL root username: root.
    -Set the password: root.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Configure IIS for PHP</h2>
<p>
1. Open IIS Manager (search IIS in the Start menu and run as Admin).
2. Click on the server name (left panel).
3. Open PHP Manager.
4. Click Register PHP and set the path to C:\PHP\php-cgi.exe.
5. Restart IIS:
    -Click Stop then Start the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Install osTicket</h2>
<p>
1. Extract osTicket v1.15.8 (osTicket-v1.15.8.zip) from the osTicket-Installation-Files folder.
2. Copy the extracted upload folder to C:\inetpub\wwwroot.
3. Rename upload to osTicket (C:\inetpub\wwwroot\osTicket).
4. Restart IIS:
    -Open IIS Manager → Stop and Start the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Configure osTicket in IIS</h2>
<p>
1. In IIS, go to Sites > Default Web Site > osTicket.
2. On the right panel, click *Browse :80.
3. The osTicket setup page will show some missing PHP extensions.
</p>
<h3>Enable Required PHP Extentions</h3>
<p>
1. In IIS, go to Sites > Default Web Site > osTicket.
2. Double-click PHP Manager.
3. Click Enable or disable an extension.
4. Enable the following extensions:
    -php_imap.dll
    -php_intl.dll
    -php_opcache.dll
5. Refresh the osTicket page in your browser to confirm the changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Setup MySQL Database for osTicket</h2>
<h3>Install HeidiSQL</h3>
<p>
1. Install HeidiSQL from the osTicket-Installation-Files folder.
2. Open HeidiSQL and create a new session with:
    -Username: root
    -Password: root
3. Click Connect.
4. Create a new database named osTicket.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Complete osTicket Installation in Browser</h2>
<p>
1. Go back to the osTicket setup page in your browser.
2. Fill in the following database settings:
    -MySQL Database: osTicket
    -MySQL Username: root
    -MySQL Password: root
3. Click Install Now!.
4. Once installation is complete, visit your osTicket admin panel:
    -Admin Login: http://localhost/osTicket/scp/login.php
    -User Portal: http://localhost/osTicket/
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Final Cleanup & Security</h2>
<p>
1. Delete the setup directory:
    - C:\inetpub\wwwroot\osTicket\setup
2. Set ost-config.php to read-only:
    - Right-click C:\inetpub\wwwroot\osTicket\include\ost-config.php > Properties.
    - Check ✅ Read-only.
</p>
<br />
I
