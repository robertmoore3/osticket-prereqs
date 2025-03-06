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
- A suitable PC or VM

<h2>Installation Steps</h2>
<h2>Download Required Files</h2>
<img src='https://github.com/user-attachments/assets/1de953dd-526f-45d7-806f-7eb50a1fd6c1' />
<ol>
<li>Download osTicket-Installation-Files.zip</li>
<li>Extract it to your Desktop—it will create a folder named osTicket-Installation-Files.</li>
</ol>
<br />


<h2>Install IIS with CGI</h2>
<img src='https://github.com/user-attachments/assets/1b28d3d4-550a-4c2b-971e-2b106eaea8fd)' />

<ol>
<li>Open Windows Features (Control Panel > Programs > Turn Windows features on or off).</li>
<li>Enable Internet Information Services (IIS).</li>
<li>Expand World Wide Web Services > Application Development Features.</li>
<li>Check ✅ CGI.</li>
<li>Click OK and restart the VM if needed.</li>
</ol>
<br />

<h2>Install Required Components</h2>
<img src="https://github.com/user-attachments/assets/58377802-47f5-490a-bc62-037b20df84bf" />

<h3>Install PHP Manager for IIS</h3>
<ol>
    <li>Open the osTicket-Installation-Files folder.</li>
    <li>Install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).</li>
</ol>
<h3>Install IIS Rewrite Module</h3>
<ol>
    <li>Install Rewrite Module (rewrite_amd64_en-US.msi).</li>
</ol>
<h3>Install PHP</h3>
<ol>
    <li>Create a new folder: C:\PHP.</li>
    <li>Extract PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into C:\PHP.</li>
</ol>
<h3>Install Visual C++ Redistributable</h3>
<ol>
    <li>1. Install VC_redist.x86.exe from the osTicket-Installation-Files folder.</li>
</ol>
<h3>Install MySQL 5.5.62</h3>
<ol>
    <li>Install MySQL 5.5.62 (mysql-5.5.62-win32.msi).</li>
    <li>Choose Typical Setup during installation.</li>
    <li>After installation, launch the MySQL Configuration Wizard:
        -Select Standard Configuration.
        -Set the MySQL root username: root.
        -Set the password: root.</li>
</ol>
<br />


<h2>Configure IIS for PHP</h2>
<img src="https://github.com/user-attachments/assets/76c0d878-55f7-4ada-9652-dbb359bd89ec" />
<ol>
    <li>Open IIS Manager (search IIS in the Start menu and run as Admin).</li>
    <li>Click on the server name (left panel).</li>
    <li>Open PHP Manager.</li>
    <li> Click Register PHP and set the path to C:\PHP\php-cgi.exe.</li>
    <li>Restart IIS:
        -Click Stop then Start the server.</li>
</ol>
<br />


<h2>Install osTicket</h2>
<img src="https://github.com/user-attachments/assets/1d2b6cef-bba2-4394-a269-23e57abbd0e6" />
<ol>
    <li>Extract osTicket v1.15.8 (osTicket-v1.15.8.zip) from the osTicket-Installation-Files folder.</li>
    <li>Copy the extracted upload folder to C:\inetpub\wwwroot.</li>
    <li>Rename upload to osTicket (C:\inetpub\wwwroot\osTicket).</li>
    <li>Restart IIS:
        -Open IIS Manager → Stop and Start the server.</li>
</ol>
<br />

<h2>Configure osTicket in IIS</h2>
<img src="https://github.com/user-attachments/assets/eca855b4-41ac-400e-8912-5d1334782c4f" />

<ol>
    <li>In IIS, go to Sites > Default Web Site > osTicket.</li>
    <li>On the right panel, click *Browse :80.</li>
    <li>The osTicket setup page will show some missing PHP extensions.</li>
</ol>
<h3>Enable Required PHP Extentions</h3>
<ol>
    <li>In IIS, go to Sites > Default Web Site > osTicket.</li>
    <li>Double-click PHP Manager.</li>
    <li>Click Enable or disable an extension.</li>
    <li>Enable the following extensions:
        -php_imap.dll
        -php_intl.dll
        -php_opcache.dll
        </li>
    <li> Refresh the osTicket page in your browser to confirm the changes.</li>
</ol>
<br />

<h2>Setup MySQL Database for osTicket</h2>
<img src="https://github.com/user-attachments/assets/e22e1b01-e06c-408c-8fea-c4138f7a1329" />

<h3>Install HeidiSQL</h3>
<ol>
<li> Install HeidiSQL from the osTicket-Installation-Files folder.</li>
<li> Open HeidiSQL and create a new session with:
    -Username: root
    -Password: root</li>
<li> Click Connect.</li>
<li> Create a new database named osTicket.</li>
</ol>
<br />

<h2>Complete osTicket Installation in Browser</h2>
<img src="https://github.com/user-attachments/assets/ea85ad07-9956-48c5-afa1-51fdce39562f" />

<ol>
<li> Go back to the osTicket setup page in your browser.</li>
<li> Fill in the following database settings:
    -MySQL Database: osTicket
    -MySQL Username: root
    -MySQL Password: root</li>
</li> Click Install Now!.</li>
<li> Once installation is complete, visit your osTicket admin panel:
    -Admin Login: http://localhost/osTicket/scp/login.php
    -User Portal: http://localhost/osTicket/</li>
</ol>
<br />

<h2>Final Cleanup & Security</h2>
<ol>
<li> Delete the setup directory:
    - C:\inetpub\wwwroot\osTicket\setup</li>
<li> Set ost-config.php to read-only:
    - Right-click C:\inetpub\wwwroot\osTicket\include\ost-config.php > Properties.
    - Check ✅ Read-only.
    </li>
</ol>
<br />
I
