# Manual-Setup-Configure-Apache-for-Windows
The "main command" in CMD (Command Prompt) on Windows depends on what you're trying to do. However, here are some common main commands you might use:

# 🔧 Basic CMD Commands
Command	Description
1. dir -	Lists files and directories in the current folder
2. cd - Changes the current directory (e.g., cd Documents)
3. cls - Clears the screen
4. exit - Closes the Command Prompt
5. echo - Displays a message or turns command echoing on/off
6. copy - Copies files from one location to another
7. del - Deletes a file
8. move - Moves a file to another location
9. mkdir - Creates a new directory
10. rmdir - Deletes a directory
11. ping - Tests network connection to a server or website
12. ipconfig - Shows network configuration (IP address, etc.)
13. tasklist - Lists running processes
14. taskkill - Kills a running process by name or PID
15. shutdown - Shuts down or restarts the computer
16. sfc /scannow - Scans and repairs system files

# To install Apache HTTP Server on Windows, follow these steps:

✅ Option 1: Easiest Way – Use XAMPP (Recommended for Beginners)
XAMPP is a free Apache distribution that includes Apache, MySQL/MariaDB, PHP, and more.

🔧 Steps:
1. Go to: https://www.apachefriends.org
2. Download XAMPP for Windows.
3. Run the installer (xampp-win32-*.exe).
4. Follow the setup wizard and install.
5. Launch the XAMPP Control Panel and click Start next to Apache.

🔍 Apache will now be running on http://localhost.

✅ Option 2: Manual Apache Installation

📥 Step 1: Download Apache Binaries
Go to: https://www.apachelounge.com/download/
Download the latest Apache HTTP Server for Windows (httpd-*.zip).

📂 Step 2: Extract Files
Extract the ZIP file to a folder, e.g., C:\Apache24.

⚙️ Step 3: Install Apache as a Service
Open Command Prompt as Administrator.

Run this command:
cd \Apache24\bin
httpd.exe -k install

▶️ Step 4: Start Apache
httpd.exe -k start

Visit http://localhost in your browser to verify Apache is running.
⚠️ Notes
If port 80 is in use (e.g., by Skype or IIS), Apache may fail to start.

You can change the port in httpd.conf:
Listen 8080
Then access it via http://localhost:8080.

Great! To configure PHP with Apache on Windows, you can do it manually (advanced) or use XAMPP (easy). Since you're going manual, here's how to integrate PHP with Apache:

# 🔧 Manual Setup: Configure PHP with Apache (Windows)

✅ Step 1: Download PHP for Windows
Go to: https://windows.php.net/download
Choose a Thread Safe version (e.g., PHP 8.x).
Download the .zip file for your system (x64 or x86).
Extract it to a folder, e.g., C:\php.

✅ Step 2: Configure Apache to Use PHP
Open Apache's config file:
C:\Apache24\conf\httpd.conf

# PHP Configuration
Add these lines at the end of the file:
LoadModule php_module "C:/php/php8apache2_4.dll"
AddHandler application/x-httpd-php .php
PHPIniDir "C:/php"
🔁 Adjust the path and filename based on your PHP version (e.g., php8apache2_4.dll).

Save and close httpd.conf.

✅ Step 3: Edit PHP Configuration
In C:\php, rename php.ini-development to php.ini.

Open php.ini and make these changes:

Enable extensions like:
extension_dir = "ext"
extension=curl
extension=mbstring
extension=mysqli
extension=pdo_mysql

Set timezone:
date.timezone = "UTC"
Replace UTC with your timezone (e.g., America/New_York).

✅ Step 4: Restart Apache
Run these commands in Admin CMD:
cd \Apache24\bin
httpd -k restart

✅ Step 5: Test PHP
Create a file in your htdocs directory (e.g., C:\Apache24\htdocs\index.php)

Add this content:
<?php phpinfo(); ?>
Visit http://localhost/index.php in your browser.

✅ If you see the PHP info page, it's working!

Perfect! Here’s how to install MySQL and phpMyAdmin, and connect them to your Apache + PHP setup on Windows.

# 🛠 Step 1: Install MySQL on Windows
🔽 Download & Install:
Go to: https://dev.mysql.com/downloads/installer/
Choose the MySQL Installer (Community) → Windows (x86, 64-bit) → Download the full installer.
Run the installer and choose "Developer Default" or "Server Only".
During setup:
Set a root password you’ll remember.
Choose default settings for port (3306) and Windows service.
✅ After installation, MySQL should run as a Windows service.

# 🛠 Step 2: Test MySQL
Open Command Prompt and type:
mysql -u root -p
Enter your password → If successful, you're in the MySQL shell.

# 🛠 Step 3: Download & Configure phpMyAdmin
🔽 Download:
Go to: https://www.phpmyadmin.net/downloads/
Download the phpMyAdmin .zip file.
Extract it to:
C:\Apache24\htdocs\phpmyadmin

# ⚙️ Step 4: Configure config.inc.php
Inside the extracted phpmyadmin folder, copy:
config.sample.inc.php → config.inc.php
Open config.inc.php and set the authentication type and password:
// $cfg['blowfish_secret'] = 'YourRandomSecret123!'; // At least 32 chars
// $cfg['Servers'][1]['auth_type'] = 'cookie';
If needed, you can hardcode the login:
// $cfg['Servers'][1]['auth_type'] = 'config';
// $cfg['Servers'][1]['user'] = 'root';
// $cfg['Servers'][1]['password'] = 'your_root_password';

# ✅ Step 5: Access phpMyAdmin
Open your browser and go to:
http://localhost/phpmyadmin
Log in using:
Username: root
Password: Your MySQL root password

# 🔐 Security Tips:
Don’t use "auth_type" = "config" in production (use "cookie").
Secure the phpmyadmin folder if you're on a public server.

# ✅ At this point, you have:

1. Apache serving PHP
2. PHP connected to MySQL
3. phpMyAdmin managing your MySQL database via web interface
