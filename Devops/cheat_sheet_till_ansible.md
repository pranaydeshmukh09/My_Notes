# 🧠 Linux Commands Cheat Sheet (DevOps with Explanation)

------------------------------------------------------------------------

## 📁 File Management

-   `ls -l` → list files with details (permissions, size, owner)
-   `ls -a` → show hidden files
-   `pwd` → show current directory path
-   `cd <dir>` → change directory
-   `cd ..` → move one level up
-   `mkdir <name>` → create a new directory
-   `rm <file>` → delete a file
-   `rm -rf <dir>` → delete directory recursively (force)
-   `cp <src> <dest>` → copy file
-   `mv <src> <dest>` → move or rename file
-   `touch <file>` → create empty file
-   `cat <file>` → display file content
-   `less <file>` → view file with scrolling
-   `head -n 10` → first 10 lines of file
-   `tail -n 10` → last 10 lines

------------------------------------------------------------------------

## 🔐 File Permissions

-   `chmod 744 file` → set permissions (owner full, others read)
-   `chmod u+x file` → add execute permission to user
-   `chmod go-w file` → remove write from group & others
-   `chown user:group file` → change file ownership

------------------------------------------------------------------------

## ⚙️ Process Management

-   `ps aux` → show all running processes
-   `ps -ef` → detailed process list
-   `top` → real-time process usage
-   `htop` → interactive process viewer

### Filtering

-   `ps aux | grep java` → find specific process
-   `ps aux | wc -l` → count processes

### Control

-   `kill <pid>` → stop process
-   `kill -9 <pid>` → force kill
-   `kill -STOP <pid>` → pause process
-   `kill -CONT <pid>` → resume process

### Priority

-   `nice -n 10 <cmd>` → start process with priority
-   `renice -n 5 -p <pid>` → change priority of running process

------------------------------------------------------------------------

## 🧠 System Monitoring

-   `top` → CPU & memory usage
-   `htop` → better UI monitoring
-   `free -h` → memory usage (human readable)
-   `df -h` → disk space usage
-   `du -sh <dir>` → directory size
-   `vmstat` → system performance stats
-   `uptime` → system load & running time

------------------------------------------------------------------------

## 📜 Logs & Monitoring

-   `tail -f /var/log/syslog` → live log tracking
-   `less /var/log/syslog` → read logs
-   `grep "error" file` → search text
-   `awk '{print $1}' file` → extract columns
-   `cut -d":" -f1 file` → split and extract data
-   `journalctl -u nginx` → logs for service
-   `journalctl -xe` → recent system errors

------------------------------------------------------------------------

## 🔧 Services (Systemctl)

-   `systemctl start nginx` → start service
-   `systemctl stop nginx` → stop service
-   `systemctl restart nginx` → restart service
-   `systemctl status nginx` → check status
-   `systemctl enable nginx` → start on boot
-   `systemctl disable nginx` → disable auto start

------------------------------------------------------------------------

## 🌐 Networking

-   `ip a` → show IP address
-   `ping google.com` → test connectivity
-   `netstat -tulnp` → open ports (old)
-   `ss -tulnp` → open ports (modern)
-   `curl <url>` → API request
-   `wget <url>` → download file

------------------------------------------------------------------------

## 📦 Package Management

-   `apt update` → update package list
-   `apt upgrade` → upgrade packages
-   `apt install nginx` → install package
-   `apt remove nginx` → remove package

------------------------------------------------------------------------

## 🔍 Searching

-   `find / -name file.txt` → search file
-   `which python` → path of command
-   `whereis nginx` → binary + config locations

------------------------------------------------------------------------

## ⚡ Scripting

-   `set -x` → debug script
-   `set -e` → exit on error
-   `set -o pipefail` → fail if any command fails

------------------------------------------------------------------------

## 🔥 Misc

-   `history` → command history
-   `clear` → clear terminal
-   `whoami` → current user
-   `id` → user details
-   `hostname` → system name

------------------------------------------------------------------------

## 🧩 Bonus

-   `crontab -e` → schedule tasks
-   `tar -cvf file.tar` → create archive
-   `tar -xvf file.tar` → extract archive
-   `zip` → compress
-   `unzip` → extract zip

---
1️⃣7️⃣ 🔧 Git & GitHub (Version Control)

👉 Used for tracking code, collaboration, and deployments

Basic Git Setup

git config --global user.name "name"
git config --global user.email "email"

Repository Setup

git init → initialize repo
git clone <repo_url> → copy repo

Daily Workflow ⭐

git status → check changes
git add . → stage all changes
git commit -m "message" → save changes
git push origin main → upload to GitHub
git pull origin main → get latest changes

Branching (Important)

git branch → list branches
git branch <name> → create branch
git checkout <branch> → switch branch
git checkout -b <name> → create + switch
git merge <branch> → merge branch

Undo / Fix Mistakes

git restore <file> → discard changes
git reset --soft HEAD~1 → undo commit (keep changes)
git reset --hard HEAD~1 → undo commit (delete changes)

💡 Real Use:

* Code backup
* Team collaboration
* CI/CD pipelines

---

1️⃣8️⃣ ⚙️ Ansible (Automation & Configuration Management)

👉 Used to automate servers, deployments, and configs

Basic Concepts ⭐

* Inventory → list of servers
* Playbook → automation file (YAML)
* Task → single action
* Module → unit of work

Inventory File Example

[web]
192.168.1.10
192.168.1.11

Basic Commands

ansible all -m ping → check connectivity
ansible all -a "uptime" → run command
ansible web -m apt -a "name=nginx state=present"

🔧 Common Modules + Important Arguments ⭐

📦 apt (Package Management)

apt:
  name: nginx
  state: present
  update_cache: yes

⚙️ service (Manage Services)

service:
  name: nginx
  state: started
  enabled: yes

📁 copy (Copy Files)

copy:
  src: index.html
  dest: /var/www/html/index.html
  owner: root
  mode: '0644'

📂 file (Manage Files/Dirs)

file:
  path: /var/www/html
  state: directory
  mode: '0755'

👤 user (User Management)

user:
  name: devops
  state: present
  groups: sudo

🌐 get_url (Download Files)

get_url:
  url: https://example.com/app.tar.gz
  dest: /tmp/app.tar.gz

Playbook Execution

ansible-playbook playbook.yml

Sample Playbook ⭐

- name: Install Nginx
  hosts: web
  become: yes

  tasks:
    - name: Install package
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start service
      service:
        name: nginx
        state: started
        enabled: yes