# System Administrator Basics

As a soon-to-be System Administrator, you'll need to be prepared with the right set of tools to manage servers, troubleshoot issues, and keep systems running smoothly. Here’s a comprehensive list of essential tools, commands, and concepts that you should have in your tool belt. These will not only enhance your ability to perform administrative tasks but also provide the flexibility to manage systems efficiently and with ease.

## **File Editors**

#### **Ed**  
**Definition**: Standard line editor.

#### **Ex**  
**Definition**: Extended line editor.

#### **Emacs**  
**Definition**: A full-screen editor, often used for programming and writing.

#### **Pico**  
**Definition**: A beginner's editor, simple and easy to use.

#### **vim**  
**Definition**: An advanced version of the vi command, more user-friendly with additional features.
- **Example**: `vim filename`  
  - **Explanation**: Opens the specified file using Vim. You can edit, delete, and navigate within the file using various commands.

- **Interactive Training**:
  - www.openvim.com  
  - www.vimgenius.com  
  - www.vim-adventures.com

#### **vi**  
**Definition**: A visual editor for editing files.
- **Example**: `vi filename`  
  - **Explanation**: Opens the specified file in the vi editor. You can use commands to navigate and edit the file.

- **Common Keys**:
  - `i`: Go into insert mode to start typing.
  - `Esc`: Exit any mode and return to command mode.
  - `a`: Advance the highlighter in insert mode, allowing you to keep typing in insert mode without switching back to command mode.
  - `r`: Replace a character at the cursor position. You have to press `r` for each character.
  - `u`: Undo the previous action.
  - `o`: Create a new line and automatically enter insert mode.
  - `d`: Delete the whole line in viewing mode.
  - `x`: Delete a single character at a time.
  - `:q!`: Quit without saving changes.
  - `:wq!`: Quit and save changes.
  - `Shift+z+z`: Quit and save.
  
- **Arrow Keys**: Move around the file (but not in insert mode).

- **Searching in vi**:
  - **Example**: `/keyword`  
  - **Explanation**: Search for a word in the file. This works when not in insert mode.

#### **sed**  
**Definition**: A command-line tool for modifying files by replacing, deleting, or transforming text.
- **Example**: `sed 's/originalword/newword/g' filename`  
  - **Explanation**: This command will replace all occurrences of `originalword` with `newword` in the file.
  
- **Find and Delete a Line**:
  - **Example**: `sed '/originalword/d' filename`  
  - **Explanation**: Deletes any line containing `originalword` from the file.
  
- **Remove Empty Lines**:
  - **Example**: `sed '/^$/d' filename`  
  - **Explanation**: Removes all empty lines from the file.

- **Remove Specific Lines**:
  - **Example**: `sed '1d' filename`  
  - **Explanation**: Removes the first line from the file.

- **Replace Tabs with Spaces**:
  - **Example**: `sed 's/\t/ /g' filename`  
  - **Explanation**: Replaces all tabs with spaces in the file.

- **Show Specific Lines**:
  - **Example**: `sed -n 12,18p filename`  
  - **Explanation**: Displays lines 12 to 18 of the file.
  
- **Substitute in vi**:
  - **Example**: `:%s/originalword/newword/`  
  - **Explanation**: Replaces `originalword` with `newword` within the vi editor.

- **In-place Editing**:
  - **Example**: `sed -i 's/originalword/newword/g' filename`  
  - **Explanation**: Replaces `originalword` with `newword` in the file directly without opening it in an editor.

---

## **User Account Management**

These commands are found in the following files:
- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`

Make sure you are root first by entering `su -`.

#### **useradd**  
**Definition**: Creates a user.  
- **Example**: `useradd username`  
  - **Explanation**: Adds a new user named `username`.

#### **groupadd**  
**Definition**: Creates a group.  
- **Example**: `groupadd groupname`  
  - **Explanation**: Creates a new group called `groupname`.

#### **usermod**  
**Definition**: Modifies user details.  
- **Example**: `usermod -G groupname username`  
  - **Explanation**: Adds a user to the specified group `groupname`.

#### **userdel**  
**Definition**: Removes a user.  
- **Example**: `userdel -r username`  
  - **Explanation**: Removes the user `username` and their home directory.

#### **groupdel**  
**Definition**: Removes a group.  
- **Example**: `groupdel groupname`  
  - **Explanation**: Deletes the group `groupname`.

#### **passwd**  
**Definition**: Sets or changes a user's password.  
- **Example**: `passwd username`  
  - **Explanation**: Sets a password for the specified user.

#### **chage**  
**Definition**: Changes password rules for a user.  
- **Example**: `chage -m 5 -M 90 -W 10 -I 3 username`  
  - **Explanation**: Changes the password expiry settings for the user `username`.

#### **su - username**  
**Definition**: Switches to a different user.  
- **Example**: `su - username`  
  - **Explanation**: Logs in as the user `username`.

#### **sudo**  
**Definition**: Run commands as the root user.  
- **Example**: `sudo command`  
  - **Explanation**: Runs a command with root privileges.

#### **who**  
**Definition**: Displays who is logged into the system.  
- **Example**: `who`  
  - **Explanation**: Shows the list of currently logged-in users.

#### **last**  
**Definition**: Shows the login history.  
- **Example**: `last`  
  - **Explanation**: Displays information about the last logged-in users.

#### **w**  
**Definition**: Shows information about users and their activity.  
- **Example**: `w`  
  - **Explanation**: Displays detailed info about logged-in users, including idle time.

#### **finger/pinky**  
**Definition**: Displays detailed information about a user.  
- **Example**: `finger username`  
  - **Explanation**: Shows information about the specified user. (Requires installation of the `finger` or `pinky` package.)

#### **id**  
**Definition**: Displays user ID and group ID.  
- **Example**: `id username`  
  - **Explanation**: Shows the ID and group information for the specified user.

#### **wall**  
**Definition**: Sends a message to all logged-in users.  
- **Example**: `wall "System maintenance starts in 10 minutes"`  
  - **Explanation**: Sends a broadcast message to all users on the system.

#### **write**  
**Definition**: Sends a message to a specific user.  
- **Example**: `write username`  
  - **Explanation**: Sends a direct message to the specified user.

---

## **What the Heck is Active Directory, LDAP, IDM, WinBIND, and OpenLDAP?**

#### **Active Directory**  
**Definition**: A directory service developed by Microsoft to manage and store information about network resources, users, and services.

#### **LDAP (Lightweight Directory Access Protocol)**  
**Definition**: A protocol used to access and manage directory services over a network.

#### **IDM (Identity Manager)**  
**Definition**: A system for managing digital identities, including their creation, deletion, and access permissions.

#### **WinBIND**  
**Definition**: A Linux service used to connect to a Windows Active Directory environment, enabling users to authenticate to a Linux system with Active Directory credentials.  
- **Example**: `winbindd`  
  - **Explanation**: Starts the WinBIND service, allowing Linux systems to authenticate users through Active Directory.

#### **OpenLDAP**  
**Definition**: An open-source implementation of the LDAP protocol.  
- **Example**: `slapd`  
  - **Explanation**: Starts the OpenLDAP server daemon, enabling LDAP communication on the system.

---

## **System Utility Commands**

#### **date**  
**Definition**: Displays or sets the system date and time.  
- **Example**: `date`  
  - **Explanation**: Shows the current system date and time.

#### **uptime**  
**Definition**: Displays how long the system has been running.  
- **Example**: `uptime`  
  - **Explanation**: Shows the current system uptime, including the number of users and system load.

#### **hostname**  
**Definition**: Shows or sets the system's hostname.  
- **Example**: `hostname`  
  - **Explanation**: Displays the current hostname of the system.

#### **uname**  
**Definition**: Displays system information such as the kernel name and version.  
- **Example**: `uname -a`  
  - **Explanation**: Shows detailed information about the kernel, including the system architecture and version.

#### **which**  
**Definition**: Locates where a command or file is stored.  
- **Example**: `which ls`  
  - **Explanation**: Finds the location of the `ls` command on your system.

#### **cal**  
**Definition**: Displays a calendar.  
- **Example**: `cal 9 1977`  
  - **Explanation**: Shows the calendar for September 1977.  
- **Example**: `cal 2016`  
  - **Explanation**: Displays the calendar for the year 2016.

#### **bc**  
**Definition**: A calculator program.  
- **Example**: `bc`  
  - **Explanation**: Opens the basic calculator. Type `quit` to exit.

---

## **Processes and Jobs**

#### **Applications**  
**Definition**: Programs that perform tasks and run as services.

#### **Script**  
**Definition**: A file containing a series of commands to be executed by the system.

#### **Process**  
**Definition**: A running program that is managed by the system.

#### **Daemon**  
**Definition**: A process that runs in the background until manually stopped.  
- **Example**: `systemctl start apache2`  
  - **Explanation**: Starts the Apache web server as a daemon.

#### **Threads**  
**Definition**: The smallest unit of a process that can be scheduled for execution.

#### **Job**  
**Definition**: A process running in the background that is controlled by the user.

#### **systemctl or service**  
**Definition**: Command used to manage system services.  
- **Example**: `systemctl start servicename.service`  
  - **Explanation**: Starts the specified service.  
- **Example**: `systemctl stop servicename.service`  
  - **Explanation**: Stops the specified service.  
- **Example**: `systemctl status servicename.service`  
  - **Explanation**: Displays the status of the specified service.  
- **Example**: `systemctl enable servicename.service`  
  - **Explanation**: Configures the service to start automatically at boot.  
- **Example**: `systemctl restart servicename.service`  
  - **Explanation**: Restarts the specified service.  
- **Example**: `systemctl reload servicename.service`  
  - **Explanation**: Reloads the service configuration.  
- **Example**: `systemctl list-units --all`  
  - **Explanation**: Lists all units, including inactive services.  
- **Example**: `systemctl poweroff`  
  - **Explanation**: Shuts down the system.  
- **Example**: `systemctl halt`  
  - **Explanation**: Immediately halts the system.  
- **Example**: `systemctl reboot`  
  - **Explanation**: Reboots the system.

#### **ps**  
**Definition**: Displays a list of currently running processes.  
- **Example**: `ps -e`  
  - **Explanation**: Shows all the running processes.  
- **Example**: `ps aux`  
  - **Explanation**: Displays detailed information about all running processes.  
- **Example**: `ps -ef`  
  - **Explanation**: Shows all running processes in full format.  
- **Example**: `ps -u username`  
  - **Explanation**: Displays processes running under a specific user.

#### **top**  
**Definition**: Displays system information and running processes in real time.  
- **Example**: `top`  
  - **Explanation**: Opens a real-time view of the processes, showing CPU and memory usage.  
- **Example**: `top -u username`  
  - **Explanation**: Displays processes running under a specific user.  
- **Example**: `press c`  
  - **Explanation**: Toggles to show full command-line details of processes.  
- **Example**: `press k`  
  - **Explanation**: Allows the user to kill a process from the top view.  
- **Example**: `press Shift+M,P`  
  - **Explanation**: Sorts processes by memory or CPU usage, respectively.

#### **kill**  
**Definition**: Terminates a process.  
- **Example**: `kill PID`  
  - **Explanation**: Kills the process with the specified PID (Process ID).  
- **Example**: `kill -l`  
  - **Explanation**: Lists all available signal types.  
- **Example**: `kill -9 PID`  
  - **Explanation**: Forcefully kills a process.  
- **Example**: `kill -15 PID`  
  - **Explanation**: Sends a SIGTERM signal to gracefully stop a process.  
- **Example**: `killall processname`  
  - **Explanation**: Kills all processes with the specified name.  
- **Example**: `pkill processname`  
  - **Explanation**: Kills processes by name.

#### **crontab**  
**Definition**: Manages cron jobs for scheduled tasks.

#### **at**  
**Definition**: Schedules a task to run once at a specified time.

---

## **Process Signals**

### **Understanding Processes and Signals**
- **Processes**: A running program that performs specific tasks on a computer system.  
- **Signals**: A short message sent to a process, designed to interrupt or control its behavior without stopping the program.

### **Types of Signals**
#### **Standard Signals**  
Predefined signals sent by the OS to control processes.

- **SIGINT (Signal Interrupt)**  
  - **Definition**: Interrupts a process.  
  - **Example**: `kill -SIGINT PID`  
    - **Explanation**: Interrupts the process with the specified PID.

- **SIGTERM (Signal Terminate)**  
  - **Definition**: Gracefully terminates a process.  
  - **Example**: `kill -SIGTERM PID`  
    - **Explanation**: Terminates the process with the specified PID, allowing it to clean up before stopping.

- **SIGKILL (Signal Kill)**  
  - **Definition**: Forcefully kills a process.  
  - **Example**: `kill -SIGKILL PID`  
    - **Explanation**: Immediately terminates the process, without allowing it to clean up.

- **SIGSTOP (Signal Stop)**  
  - **Definition**: Pauses a running process.  
  - **Example**: `kill -SIGSTOP PID`  
    - **Explanation**: Suspends the process with the specified PID.

- **SIGCONT (Signal Continue)**  
  - **Definition**: Resumes a paused process.  
  - **Example**: `kill -SIGCONT PID`  
    - **Explanation**: Resumes a previously stopped process.

- **SIGSEGV (Signal Segmentation Fault)**  
  - **Definition**: Indicates an invalid memory access or segmentation fault.  
  - **Example**: `kill -SIGSEGV PID`  
    - **Explanation**: Sends a segmentation fault signal to the process, typically due to accessing invalid memory.

#### **Real-Time Signals**  
Signals that allow additional information to be sent along with the signal.
- **SIGRTMIN**  
  - **Definition**: Marks the beginning of real-time signals.

- **SIGRTMAX**  
  - **Definition**: Marks the end of real-time signals.

- **Intermediate Signals**  
  - **Definition**: Signals that fall between SIGRTMIN and SIGRTMAX.
