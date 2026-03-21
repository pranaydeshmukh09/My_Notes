
## 1. User Management
Linux is a multi-user system. Access is managed through three main categories:
* **User:** The individual account (Owner).
* **Group:** A collection of users with shared permissions.
* **Other:** All other users on the system.


### Essential User Commands
| # | Command | Description |
| 1 | `useradd` | Adds a user (Basic command, doesn't create home dir by default). |
| 2 | `adduser` | Adds a user interactively (More detailed, creates home dir/folders). |
| 3 | `passwd <user>` | Assigns or changes a password for a user. |
| 4 | `passwd -n 90` | Forces the user to change password every 90 days. |
| 5 | `passwd -l` | **Lock** a user account. |
| 6 | `passwd -u` | **Unlock** a user account. |
| 7 | `userdel` | Delete a user account. |
| 8 | `sudo -i` / `sudo su -` | Switch from a regular user to the **Root** (superuser). |
| 9 | `sudo su - <name>` | Switch from Root to a specific user. |

### System Identity Files
* `vim /etc/passwd`: Lists all created users and their details.
* `vim /etc/shadow`: Stores encrypted passwords (hidden for security).

----------------------------------------------------------------------------

## 2. Group Management
Groups allow you to manage multiple users' permissions simultaneously.

* **Create Group:** `groupadd <groupname>`
* **List Groups:** `cat /etc/group`
* **Add User to Group:** `usermod -aG <groupname> <username>`

----------------------------------------------------------------------------

## 3. File Management
### Directory & File Navigation
* `ls`: List files and directories.
* `pwd`: Show current directory path.
* `cd ..`: Move one level up.
* `mkdir <name>`: Create a new directory.
* `rmdir <name>`: Remove an empty directory.
* `touch <file>`: Create an empty file.
* `rm <file>`: Delete a file.
* `rm -rf <dir>`: Forcefully and recursively delete a folder and its contents.
* `cp <src> <dest>`: Copy files/folders.
* `mv <src> <dest>`: Move or rename files/folders.
* `cat <file>`: Display file content in the terminal.

### VI / VIM Editor Shortcuts
1. **Open:** `vim <filename>`
2. **Insert Mode:** Press `i` (to start typing).
3. **Command Mode:** Press `Esc` (to stop typing).
4. **Save & Quit:** Type `:wq!` and hit Enter.
5. **Quit without saving:** Type `:q!` and hit Enter.

----------------------------------------------------------------------------

## 4. File Permissions
Permissions are calculated using a numbering system:
* **Read (r)** = 4
* **Write (w)** = 2
* **Execute (x)** = 1



**Example:** `chmod 776 demo.txt`
- **7 (4+2+1):** User (Owner) has Full Access.
- **7 (4+2+1):** Group has Full Access.
- **6 (4+2):** Others have Read/Write access only.

**Ownership:**
* `chown <newuser> <filename>`: Change the owner of a file.

----------------------------------------------------------------------------

## 5. Process Management
### Viewing Processes
* `ps`: View processes running in the current shell.
* `ps aux`: View **all** running processes with CPU/Memory usage.
* `ps aux | nl`: View processes with line numbers.
* `ps aux | wc -l`: Count total number of running processes.
* `ps aux | grep <name>`: Filter for a specific process (e.g., `grep java`).
* `ps -ef`: View processes with Parent Process ID (PPID) details.

### Controlling Processes
* `kill <pid>`: Stop a process gracefully.
* `kill -9 <pid>`: **Forcefully** kill a process.
* `kill -stop <pid>`: Pause/Suspend a process.
* `kill -cont <pid>`: Resume a paused process.

**Priority (Niceness):**
* `renice -n -5 -p <pid>`: Prioritize a process (higher priority).
* `renice -n 10 -p <pid>`: Deprioritize a process (lower priority).

----------------------------------------------------------------------------

## 6. Services & Monitoring
**Services:** Background processes (daemons) that manage system functions.
* `systemctl`: Primary command to manage and list services.

### System Health Checks
* `top` / `htop`: Real-time monitoring of CPU/RAM and processes.
* `uptime`: Shows how long the system has been active.
* `free -m`: Check Free/Used memory in MB.
* `df -h`: Check Disk Space usage (human-readable).
* `lsblk`: List all block devices (disks and partitions).
* `fdisk -l`: List disk partition tables.

----------------------------------------------------------------------------

## 7. Networking & Infrastructure
**SSH (Secure Shell):** Used to connect securely to a remote server.

### Traffic Flow Architecture
`Client PC` ➔ `Router` ➔ `Internet Gateway` ➔ `Routing Table` ➔ `Load Balancer` ➔ `App Servers`



> **Note:** Networking notes continue from Day 12 (Deepika Ma'am).