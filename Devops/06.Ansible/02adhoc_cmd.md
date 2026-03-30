# Ansible Ad-Hoc Commands Cheat Sheet

## 1️⃣ Command Structure
```
ansible <hosts> -i <inventory> -m <module> -a "<arguments>" -b
```

### Explanation:
- `<hosts>` → Which host(s) to target (all, webservers, etc.)
- `<inventory>` → Your inventory file (e.g., `-i ~/ansible/inventory`)
- `<module>` → The action to perform (file, shell, apt, etc.)
- `<arguments>` → How the module does it (key=value)
- `-b` → Run as root / sudo if needed

---

## 2️⃣ Flags

| Flag | Meaning | Notes |
|------|--------|------|
| -i | Inventory file | Specifies which hosts to target |
| -m | Module | What action to perform |
| -a | Arguments | How the module performs the action (key=value) |
| -b | Become / sudo | Use if task requires root privileges |

---

## 3️⃣ Arguments (-a)

**Format:** `key=value`

### Examples per module:

| Module | Example Arguments |
|--------|------------------|
| file | path=/var/pranay_dir state=directory |
| apt | name=nginx state=present |
| shell | cmd="ls -l /var" |
| copy | src=/home/ubuntu/file.txt dest=/tmp/file.txt |

💡 **Tip:** Always use absolute paths and keep key=value pairs simple.

---

## 4️⃣ Common Modules

| Module | What it does |
|--------|--------------|
| ping | Test connectivity |
| file | Create/delete directories or files |
| apt/yum | Install packages |
| shell | Run shell commands |
| copy | Copy files to remote hosts |
| service | Start/stop/restart services |
| user | Manage users |

---

## 5️⃣ Examples

### Ping all hosts
```
ansible all -i ~/ansible/inventory -m ping -b
```

### Create a directory
```
ansible all -i ~/ansible/inventory -m file -a "path=/var/pranay_dir state=directory" -b
```

### Install nginx
```
ansible all -i ~/ansible/inventory -m apt -a "name=nginx state=present" -b
```

### Run shell command
```
ansible all -i ~/ansible/inventory -m shell -a "ls -l /var" -b
```

### Copy a file
```
ansible all -i ~/ansible/inventory -m copy -a "src=/home/ubuntu/file.txt dest=/tmp/file.txt" -b
```
