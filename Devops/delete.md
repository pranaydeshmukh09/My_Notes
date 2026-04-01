1️⃣ Git Commands
----------------

### **Basic Setup**

`   # Set username and emailgit config --global user.name "Your Name"git config --global user.email "your.email@example.com"# Check configurationgit config --list   `

### **Repository Operations**

`# Initialize a repositorygit init# Clone a repositorygit clone` 

### **Working with Changes**

`   # Check statusgit status# Add files to staginggit add        # single filegit add .            # all files# Commit changesgit commit -m "Commit message"git commit -a -m "Commit message"   # Commit all changes without staging   `

### **Branching**

`# List branchesgit branch# Create a new branchgit branch # Switch branchgit checkout # Create & switch in one commandgit checkout -b` 

### **Merging & History**

`   # Merge branch into current branchgit merge # Show commit historygit loggit log --oneline   `

### **Remote Repositories**

`   # Add remote repositorygit remote add origin # Push branch to remotegit push -u origin # Pull latest changesgit pull origin # Fetch updates without merginggit fetch   `

2️⃣ GitHub Commands & Workflow
------------------------------

### **Fork & Pull Requests**

*   Fork: Copy someone else’s repo to your GitHub account.
    
*   Pull Request: Request to merge your changes to the original repo.
    

### **Cloning & Working**

`# Clone your forked repogit clone` 

### **Sync Fork**

`   # Add upstream (original repo)git remote add upstream # Fetch updates from original repogit fetch upstream# Merge upstream changes into your branchgit merge upstream/main   `

3️⃣ Ansible Commands
--------------------

### **Ad-Hoc Command Syntax**

`   ansible  -i  -m  -a "" -b   `

**Explanation**:

*   → Target host(s) (all, webservers, etc.)
    
*   → Inventory file path
    
*   → Action to perform (file, shell, apt, etc.)
    
*   → Module-specific parameters
    
*   \-b → Become (sudo)
    

### **Ansible Modules Quick Reference**

#### **1\. ping module –** Check if target hosts are reachable

`   ansible all -i ~/ansible/inventory -m ping   `

**Arguments:**

*   data="any\_text" → Optional message sent back
    

#### **2\. shell / command module –** Run shell commands on remote hosts

`   ansible all -i ~/ansible/inventory -m shell -a "uptime"   `

**Arguments:**

*   cmd="command" → Command to execute
    
*   chdir="/path" → Change directory first
    
*   creates="/path/file" → Skip if file exists
    
*   removes="/path/file" → Skip if file missing
    

#### **3\. file module –** Create, remove, or manage files and directories

`   ansible all -i ~/ansible/inventory -m file -a "path=/tmp/devops.txt state=absent" -b   `

**Arguments:**

*   path="/path/to/file\_or\_dir" → Target path
    
*   state=absent|directory|file|touch|link → Desired state
    
*   mode="0644" → File permissions
    
*   owner="user" → File owner
    
*   group="group" → File group
    

#### **4\. copy module –** Copy files from control node to managed nodes

`   ansible all -i ~/ansible/inventory -m copy -a "src=/etc/hosts dest=/tmp/hosts_copy" -b   `

**Arguments:**

*   src="/path/source\_file" → Source file
    
*   dest="/path/dest\_file" → Destination path
    
*   owner="user" → File owner
    
*   group="group" → File group
    
*   mode="0644" → File permissions
    
*   backup=yes|no → Backup existing file
    

#### **5\. service module –** Start, stop, or manage services on hosts

`   ansible all -i ~/ansible/inventory -m service -a "name=nginx state=started enabled=yes" -b   `

**Arguments:**

*   name="service\_name" → Service to manage
    
*   state=started|stopped|restarted|reloaded → Desired state
    
*   enabled=yes|no → Enable at boot
    

#### **6\. yum / apt module –** Install, update, or remove packages

`   ansible all -i ~/ansible/inventory -m yum -a "name=httpd state=latest" -bansible all -i ~/ansible/inventory -m apt -a "name=nginx state=present" -b   `

**Arguments:**

*   name="package\_name" → Package name
    
*   state=present|absent|latest → Desired state
    
*   update\_cache=yes|no → Refresh package cache
    

#### **7\. user module –** Create or manage users on hosts

`   ansible all -i ~/ansible/inventory -m user -a "name=devops state=present password=" -b   `

**Arguments:**

*   name="username" → User name
    
*   state=present|absent → Create or remove user
    
*   password="" → Set password
    
*   shell="/bin/bash" → Login shell
    
*   groups="group1,group2" → Add user to groups
    
*   append=yes|no → Append groups without removing
    

✅ **Tips:**

*   Always use -i if inventory is not default.
    
*   Test commands first with ping.
    
*   Group hosts in inventory for easier management.
    
*   Use YAML playbooks for repetitive tasks.