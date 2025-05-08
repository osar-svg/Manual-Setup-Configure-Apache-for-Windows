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
