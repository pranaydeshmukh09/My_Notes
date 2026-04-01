# 🧠 Linux Commands Cheat Sheet (Proper DevOps Sequence)

👉 Think: “I logged into a server… now what?”

## 1️⃣ 🧍 Basic Info (Start Here Always)
- `whoami` → current user  
- `id` → user + groups  
- `hostname` → system name  
- `pwd` → current directory  
- `history` → previous commands  

## 2️⃣ 📁 Navigation & File Management
- `ls -l` → list files  
- `ls -a` → hidden files  
- `cd <dir>` → change directory  
- `cd ..` → go back  
- `mkdir <name>` → create directory  
- `touch <file>` → create file  
- `cp <src> <dest>` → copy  
- `mv <src> <dest>` → move/rename  
- `rm <file>` → delete file  
- `rm -rf <dir>` → delete directory  

## 3️⃣ 📄 File Viewing & Reading
- `cat <file>` → full content  
- `less <file>` → scroll file  
- `head -n 10` → first lines  
- `tail -n 10` → last lines  
- `tail -f file` → live logs  

## 4️⃣ 🔐 Permissions & Ownership
- `chmod 744 file` → set permissions  
- `chmod u+x file` → add execute  
- `chmod go-w file` → remove write  
- `chown user:group file` → change owner  

## 5️⃣ 🔍 Searching (Files + Commands)
- `find / -name file.txt` → search file  
- `which python` → command path  
- `whereis nginx` → binary location  

## 6️⃣ 🔗 Text Processing ⭐
- `grep "error" file` → search text  
- `awk '{print $1}' file` → extract data  
- `sed 's/old/new/g' file` → replace text  
- `cut -d":" -f1 file` → split data  
- `sort file` → sort  
- `uniq` → remove duplicates  

## 7️⃣ ⚙️ Process Management
- `ps aux`  
- `top`  
- `kill <pid>`  
- `nice / renice`  

## 8️⃣ 🧠 System Monitoring
- `free -h`  
- `df -h`  
- `du -sh`  
- `uptime`  

## 9️⃣ 📜 Logs Monitoring ⭐
- `tail -f /var/log/syslog`  
- `journalctl -xe`  

## 🔟 🔧 Services
- `systemctl start nginx`  
- `systemctl status nginx`  

## 1️⃣1️⃣ 🌐 Networking
- `ip a`  
- `ping`  
- `curl`  

## 1️⃣2️⃣ 📦 Package Management
- `apt install nginx`  

## 1️⃣3️⃣ 👤 User Management
- `useradd`  
- `usermod`  

## 1️⃣4️⃣ 📦 Archiving
- `tar -czvf`  
- `unzip`  

## 1️⃣5️⃣ 💽 Disk
- `lsblk`  
- `mount`  

## 1️⃣6️⃣ ⚡ Scripting
- `set -e`  
- `set -x`  

---

## 1️⃣7️⃣ 🔧 Git & GitHub

- `git init`  
- `git add .`  
- `git commit -m "msg"`  
- `git push`  
- `git pull`  

---

## 1️⃣8️⃣ ⚙️ Ansible

### Modules + Arguments

#### apt
- name  
- state  
- update_cache  

#### service
- name  
- state  
- enabled  

#### copy
- src  
- dest  
- owner  
- mode  

#### file
- path  
- state  
- mode  

#### user
- name  
- state  
- groups  

#### get_url
- url  
- dest  

---

💡 DevOps Flow: Manual → Git → Automation 🚀