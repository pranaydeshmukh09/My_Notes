# DevOps Commands Reference

---

## 1️⃣ Git Commands

### Basic Setup
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list
Repository Operations
git init
git clone <repo_url>
Working with Changes
git status
git add <file>       # single file
git add .            # all files
git commit -m "Commit message"
git commit -a -m "Commit message"   # Commit all changes without staging
Branching
git branch
git branch <branch_name>
git checkout <branch_name>
git checkout -b <branch_name>      # Create & switch
Merging & History
git merge <branch_name>
git log
git log --oneline
Remote Repositories
git remote add origin <repo_url>
git push -u origin <branch_name>
git pull origin <branch_name>
git fetch
2️⃣ GitHub Commands & Workflow
Fork: Copy someone else’s repo to your GitHub account
Pull Request: Request to merge your changes to the original repo
git clone <forked_repo_url>
git remote add upstream <original_repo_url>
git fetch upstream
git merge upstream/main
3️⃣ Ansible Commands
Ad-Hoc Command Syntax
ansible <hosts> -i <inventory> -m <module> -a "<arguments>" -b

Explanation:

<hosts> → Target host(s) (all, webservers, etc.)
<inventory> → Inventory file path
<module> → Action to perform (file, shell, apt, etc.)
<arguments> → Module-specific parameters
-b → Become (sudo)
Ansible Modules Quick Reference
1. ping module – Check if target hosts are reachable
ansible all -i ~/ansible/inventory -m ping

Arguments: data="any_text" → Optional message sent back

2. shell / command module – Run shell commands on remote hosts
ansible all -i ~/ansible/inventory -m shell -a "uptime"

Arguments:

cmd="command" → Command to execute
chdir="/path" → Change directory before running
creates="/path/file" → Skip if file exists
removes="/path/file" → Skip if file missing
3. file module – Create, remove, or manage files and directories
ansible all -i ~/ansible/inventory -m file -a "path=/tmp/devops.txt state=absent" -b

Arguments:

path="/path/to/file_or_dir" → Target path
state=absent|directory|file|touch|link → Desired state
mode="0644" → File permissions
owner="user" → File owner
group="group" → File group
4. copy module – Copy files from control node to managed nodes
ansible all -i ~/ansible/inventory -m copy -a "src=/etc/hosts dest=/tmp/hosts_copy" -b

Arguments:

src="/path/source_file" → Source file
dest="/path/dest_file" → Destination path
owner="user" → File owner
group="group" → File group
mode="0644" → File permissions
backup=yes|no → Backup existing file
5. service module – Start, stop, or manage services on hosts
ansible all -i ~/ansible/inventory -m service -a "name=nginx state=started enabled=yes" -b

Arguments:

name="service_name" → Service to manage
state=started|stopped|restarted|reloaded → Desired state
enabled=yes|no → Enable at boot
6. yum / apt module – Install, update, or remove packages
ansible all -i ~/ansible/inventory -m yum -a "name=httpd state=latest" -b
ansible all -i ~/ansible/inventory -m apt -a "name=nginx state=present" -b

Arguments:

name="package_name" → Package name
state=present|absent|latest → Desired state
update_cache=yes|no → Refresh package cache
7. user module – Create or manage users on hosts
ansible all -i ~/ansible/inventory -m user -a "name=devops state=present password=<hash>" -b

Arguments:

name="username" → User name
state=present|absent → Create or remove user
password="<hashed_password>" → Set password
shell="/bin/bash" → Login shell
groups="group1,group2" → Add user to groups
append=yes|no → Append groups without removing