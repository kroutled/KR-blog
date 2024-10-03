### **File and Directory Navigation**

|Command|Description|
|---|---|
|`pwd`|Print working directory (shows your current directory).|
|`ls`|List files and directories in the current directory.|
|`ls -l`|List in long format (permissions, owner, size, etc.).|
|`ls -a`|Show hidden files (those starting with a dot).|
|`cd directory`|Change directory to `directory`.|
|`cd ..`|Move up one directory level.|
|`cd ~`|Go to the home directory.|
|`cd -`|Go back to the previous directory.|

### **File and Directory Operations**

|Command|Description|
|---|---|
|`touch filename`|Create a new empty file or update a file's timestamp.|
|`mkdir dirname`|Create a new directory.|
|`cp source destination`|Copy a file or directory.|
|`cp -r source destination`|Recursively copy a directory and its contents.|
|`mv source destination`|Move or rename a file or directory.|
|`rm filename`|Remove a file.|
|`rm -r directory`|Remove a directory and its contents recursively.|
|`rm -f filename`|Force remove a file (ignore nonexistent files and no prompts).|
|`rmdir dirname`|Remove an empty directory.|
|`cat filename`|Display the contents of a file.|
|`less filename`|View the contents of a file page by page (use `q` to quit).|
|`head filename`|Display the first 10 lines of a file.|
|`tail filename`|Display the last 10 lines of a file.|
|`tail -f filename`|Continuously output new lines as they are added to a file (useful for logs).|

### **Permissions and Ownership**

|Command|Description|
|---|---|
|`chmod permissions filename`|Change the file permissions (e.g., `chmod 755 filename`).|
|`chown user:group filename`|Change the owner and group of a file or directory.|
|`chmod -R permissions directory`|Recursively change permissions for a directory and its contents.|
|`chown -R user:group directory`|Recursively change ownership of a directory and its contents.|

### **Search and Find**

|Command|Description|
|---|---|
|`find /path -name "filename"`|Find files by name starting at the given path.|
|`find /path -type f -name "*.txt"`|Find all `.txt` files starting from the given path.|
|`grep "text" filename`|Search for a string inside a file.|
|`grep -r "text" /path`|Recursively search for a string in files within a directory.|
|`grep -i "text" filename`|Search for a string inside a file (case insensitive).|
|`locate filename`|Find the location of a file (faster than `find`, requires indexing).|

### **File Archiving and Compression**

|Command|Description|
|---|---|
|`tar -cvf archive.tar file1 file2`|Create a tarball (archive) from multiple files.|
|`tar -xvf archive.tar`|Extract a tarball.|
|`tar -czvf archive.tar.gz /path/to/dir`|Create a compressed `.tar.gz` archive of a directory.|
|`tar -xzvf archive.tar.gz`|Extract a `.tar.gz` archive.|
|`gzip filename`|Compress a file with gzip.|
|`gunzip filename.gz`|Decompress a `.gz` file.|
|`zip archive.zip file1 file2`|Create a zip archive of multiple files.|
|`unzip archive.zip`|Extract a zip archive.|

### **Disk and Directory Usage**

|Command|Description|
|---|---|
|`df -h`|Display disk space usage in a human-readable format.|
|`du -sh directory`|Display the size of a directory.|
|`du -h --max-depth=1 /path`|Show sizes of files and directories in the specified path.|
|`lsblk`|List all block devices (disks and partitions).|

### **Process Management**

|Command|Description|
|---|---|
|`ps aux`|Show all running processes.|
|`top`|Display real-time system resource usage.|
|`htop`|Interactive system monitor (more user-friendly than `top`).|
|`kill PID`|Kill a process by its Process ID (PID).|
|`kill -9 PID`|Force kill a process.|
|`killall processname`|Kill all processes with the given name.|
|`jobs`|List background jobs.|
|`bg`|Resume a stopped job in the background.|
|`fg`|Bring a background job to the foreground.|

### **Networking**

|Command|Description|
|---|---|
|`ifconfig`|Show network interfaces and IP addresses (deprecated, use `ip` instead).|
|`ip a`|Show IP addresses and network interfaces.|
|`ping hostname`|Send ICMP echo requests to check network connectivity.|
|`curl URL`|Make a network request to a URL and display the response.|
|`wget URL`|Download a file from the web.|
|`netstat -tuln`|Show listening ports and services.|
|`ss -tuln`|Display open ports (alternative to `netstat`).|
|`scp user@host:/path/to/file /local/path`|Securely copy files from a remote host to local machine.|
|`ssh user@host`|Connect to a remote machine via SSH.|
|`traceroute hostname`|Show the route packets take to a network host.|

### **Package Management**

|Command|Description|
|---|---|
|`sudo apt update`|Update the package list (Ubuntu/Debian).|
|`sudo apt upgrade`|Upgrade all installed packages.|
|`sudo apt install package`|Install a package (Ubuntu/Debian).|
|`sudo apt remove package`|Remove a package (Ubuntu/Debian).|
|`sudo yum install package`|Install a package (RHEL/CentOS/Fedora).|
|`sudo dnf install package`|Install a package (Fedora).|

### **Permissions and Users**

|Command|Description|
|---|---|
|`sudo command`|Run a command as superuser (root).|
|`sudo -i`|Switch to the root user account.|
|`whoami`|Show the current logged-in user.|
|`su - username`|Switch to another user.|
|`adduser username`|Create a new user.|
|`passwd username`|Change a user's password.|
|`groups`|Show which groups the current user belongs to.|
|`userdel username`|Delete a user.|

### **Text Editing and Viewing**

|Command|Description|
|---|---|
|`nano filename`|Edit a file with Nano text editor.|
|`vim filename`|Edit a file with Vim text editor.|
|`echo "text" > filename`|Write text to a file (overwrite).|
|`echo "text" >> filename`|Append text to a file.|
|`cat filename`|View the contents of a file.|
|`more filename`|View a file one page at a time (press space to continue).|
|`less filename`|Similar to `more` but allows backward navigation.|

### **System Information**

| Command    | Description                                                          |
| ---------- | -------------------------------------------------------------------- |
| `uname -a` | Display information about the system (kernel version, architecture). |
| `hostname` | Show or set the system's hostname.                                   |
| `uptime`   | Display how long the system has been running.                        |
| `date`     | Display or set the system date and time.                             |
| `who`      | Show who is logged into the system.                                  |
| `dmesg`    | Display system and kernel messages.                                  |
| `free -h`  | Show free and used memory.                                           |
| `df -h`    | Show available disk space on mounted filesystems.                    |