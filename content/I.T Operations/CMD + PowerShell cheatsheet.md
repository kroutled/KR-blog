### **File and Directory Navigation (CMD & PowerShell)**

|Command (CMD/PowerShell)|Description|
|---|---|
|`cd`|Display the current directory or change the directory.|
|`cd \path\to\directory`|Change to a specified directory.|
|`cd ..`|Move up one directory level.|
|`dir`|List files and directories in the current directory.|
|`ls` (PowerShell)|List files and directories in the current directory.|
|`pwd` (PowerShell)|Print working directory (current location).|

### **File and Directory Operations (CMD & PowerShell)**

|Command|Description|
|---|---|
|`md dirname` or `mkdir dirname`|Create a new directory.|
|`rd dirname` or `rmdir dirname`|Remove an empty directory.|
|`del filename` or `rm filename`|Delete a file.|
|`copy source destination`|Copy a file to another location.|
|`xcopy source destination`|Copy files and directories (can be recursive).|
|`move source destination`|Move or rename a file or directory.|
|`ren oldname newname`|Rename a file or directory.|
|`type filename`|Display the contents of a file.|
|`more filename`|Display a file one screen at a time.|
|`cls`|Clear the screen.|

### **Permissions and Ownership (CMD & PowerShell)**

|Command|Description|
|---|---|
|`icacls filename`|Display or modify file permissions.|
|`icacls filename /grant user:F`|Grant full control permission to a user for a file.|
|`takeown /f filename`|Take ownership of a file.|
|`attrib +r filename`|Make a file read-only.|
|`attrib -r filename`|Remove the read-only attribute from a file.|

### **Search and Find (CMD & PowerShell)**

|Command|Description|
|---|---|
|`find "text" filename`|Search for a string in a file (CMD).|
|`Select-String -Pattern "text" -Path filename`|Search for a string in a file (PowerShell).|
|`dir /s filename`|Search for a file in the current directory and subdirectories (CMD).|
|`Get-ChildItem -Recurse -Filter "filename"`|Search for a file recursively (PowerShell).|

### **File Archiving and Compression (CMD & PowerShell)**

|Command (CMD/PowerShell)|Description|
|---|---|
|`compact /c filename`|Compress a file (NTFS compression).|
|`compact /u filename`|Uncompress a file.|
|`tar -cvf archive.tar file1 file2`|Create a tarball (PowerShell).|
|`tar -xvf archive.tar`|Extract a tarball (PowerShell).|

### **Disk and Directory Usage (CMD & PowerShell)**

|Command|Description|
|---|---|
|`dir`|List files and directories.|
|`dir /a`|Show hidden and system files.|
|`tree`|Display a directory tree structure.|
|`fsutil volume diskfree C:`|Display disk space information for drive C:.|
|`Get-PSDrive` (PowerShell)|Display available drives and their usage.|

### **Process Management (CMD & PowerShell)**

|Command|Description|
|---|---|
|`tasklist`|List all running processes (CMD).|
|`Stop-Process -Name processname`|Terminate a process by name (PowerShell).|
|`taskkill /PID pid`|Kill a process by PID (CMD).|
|`taskkill /IM processname /F`|Force kill a process by name (CMD).|
|`Get-Process` (PowerShell)|List all running processes (PowerShell).|

### **Networking (CMD & PowerShell)**

|Command|Description|
|---|---|
|`ipconfig`|Display network interface information and IP addresses.|
|`ping hostname`|Send ICMP echo requests to check network connectivity.|
|`tracert hostname`|Trace the route packets take to a network host (CMD).|
|`Test-Connection hostname`|Trace the route packets take (PowerShell equivalent).|
|`nslookup domain`|Query DNS information for a domain.|
|`netstat -an`|Show network connections, listening ports, and status.|

### **User and Group Management (CMD & PowerShell)**

|Command|Description|
|---|---|
|`net user`|List all users.|
|`net user username`|Display information about a user.|
|`net user username password /add`|Create a new user with a password.|
|`net localgroup groupname`|List all members of a group.|
|`net localgroup groupname username /add`|Add a user to a group.|
|`net localgroup groupname username /delete`|Remove a user from a group.|

### **Text Editing and Viewing (CMD & PowerShell)**

|Command|Description|
|---|---|
|`notepad filename`|Open a file in Notepad.|
|`echo text > filename`|Write text to a file (overwrite).|
|`echo text >> filename`|Append text to a file.|
|`type filename`|Display the contents of a file (CMD).|
|`gc filename` or `Get-Content filename`|Display the contents of a file (PowerShell).|

### **System Information (CMD & PowerShell)**

|Command|Description|
|---|---|
|`systeminfo`|Display detailed system information.|
|`hostname`|Display the computer's hostname.|
|`ver`|Display the Windows version.|
|`wmic os get caption`|Display the operating system version.|
|`Get-ComputerInfo` (PowerShell)|Display detailed system information (PowerShell).|
|`whoami`|Show the current logged-in user.|

### **Task Scheduling and Services (CMD & PowerShell)**

|Command|Description|
|---|---|
|`schtasks /query`|List scheduled tasks.|
|`schtasks /create`|Create a new scheduled task.|
|`net start servicename`|Start a service.|
|`net stop servicename`|Stop a service.|
|`Get-Service` (PowerShell)|List all services.|

### **Package Management (PowerShell)**

|Command|Description|
|---|---|
|`Install-Package`|Install a package (requires `PackageManagement` module).|
|`Get-Package`|List installed packages.|
|`Uninstall-Package`|Uninstall a package.|

### **Other Useful Commands**

|Command|Description|
|---|---|
|`cls`|Clear the screen.|
|`exit`|Exit the command prompt or PowerShell session.|
|`shutdown /s /t 0`|Shutdown the computer.|
|`shutdown /r /t 0`|Restart the computer.|

### **Navigation and Help (CMD & PowerShell)**

|Command|Description|
|---|---|
|`help` or `command /?`|Display help for a command.|
|`Get-Help cmdlet` (PowerShell)|Get help for a PowerShell cmdlet.|
|`Get-Command` (PowerShell)|List available commands in PowerShell.|