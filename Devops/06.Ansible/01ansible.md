# Ansible Notes

## 1. Introduction
- **Ansible**: Open-source IT automation tool for configuration management, application deployment, and orchestration.
- **Agentless**: No agent required on target machines; uses SSH.
- **Written in**: Python
- **Inventory**: File that contains hosts and groups.

## 2. Installation
```bash
# On Ubuntu
sudo apt update
sudo apt install ansible -y

# Check version
ansible --version
```

## 3. Inventory
- **Static Inventory**: Simple text file with IPs or hostnames.
```
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
192.168.1.20
```
- **Dynamic Inventory**: Uses scripts or cloud plugins (AWS, GCP, etc.)

- **Test Connectivity**
```bash
ansible all -m ping -i inventory
```

## 4. Ad-Hoc Commands
- **Ping all hosts**
```bash
ansible all -m ping -i inventory
```
- **Run command**
```bash
ansible webservers -m shell -a "uptime" -i inventory
```
- **Copy file**
```bash
ansible webservers -m copy -a "src=./index.html dest=/var/www/html/" -i inventory
```

## 5. Playbooks
- Written in **YAML**
- Structure:
```yaml
---
- name: Example Playbook
  hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
```
- Run playbook:
```bash
ansible-playbook playbook.yml -i inventory
```

## 6. Modules
- **Common modules**
  - `apt` / `yum` → package management
  - `copy` → copy files
  - `file` → create/remove files/directories
  - `service` → manage services
  - `command` / `shell` → run commands
  - `git` → clone git repos

## 7. Variables
```yaml
vars:
  package_name: nginx

tasks:
  - name: Install package
    apt:
      name: "{{ package_name }}"
      state: present
```

## 8. Handlers
- Used to perform actions only when notified
```yaml
handlers:
  - name: restart nginx
    service:
      name: nginx
      state: restarted
```

## 9. Roles
- Folder structure:
```
roles/
  webserver/
    tasks/main.yml
    handlers/main.yml
    vars/main.yml
    templates/
```
- Run using:
```yaml
roles:
  - webserver
```

## 10. Templates
- **Jinja2 templates**:
```
server {
  listen 80;
  server_name {{ domain_name }};
}
```
- Copy template:
```yaml
- name: Deploy nginx config
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/sites-available/default
```

## 11. Facts
- Gather system information:
```bash
ansible all -m setup -i inventory
```

## 12. Best Practices
1. Use **roles** for modularity.
2. Keep **inventory** organized by groups.
3. Use **handlers** for service restarts.
4. Version control your **playbooks** with Git.
5. Avoid running **ad-hoc commands** on production directly.

## 13. Useful Commands
```bash
ansible-doc -l              # List all modules
ansible-doc <module_name>   # Get module info
ansible-vault create secret.yml  # Encrypt file
ansible-playbook --check    # Dry run
ansible-playbook --diff     # Show changes
```

## 14. Summary
- Ansible = automation + orchestration + agentless
- Inventory → Hosts
- Modules → Actions
- Playbooks → YAML automation
- Roles → Modular design
- Templates → Dynamic config
