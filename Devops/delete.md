1️⃣7️⃣ 🔧 Git & GitHub (Version Control)

👉 Used for tracking code, collaboration, and deployments

🔹 Basic Git Setup

git config --global user.name "name"

git config --global user.email "email"

🔹 Repository Setup

git init # initialize repo

git clone \# copy repo

🔹 Daily Workflow ⭐

git status # check changes

git add . # stage all changes

git commit -m "message" # save changes

git push origin main # upload to GitHub

git pull origin main # get latest changes

🔹 Branching (Important)

git branch # list branches

git branch \# create branch

git checkout \# switch branch

git checkout -b \# create + switch

git merge \# merge branch

🔹 Undo / Fix Mistakes

git restore \# discard changes

git reset --soft HEAD~1 # undo commit (keep changes)

git reset --hard HEAD~1 # undo commit (delete changes)

💡 Real Use

Code backup

Team collaboration

CI/CD pipelines

\---

1️⃣8️⃣ ⚙️ Ansible (Automation & Configuration Management)

👉 Used to automate servers, deployments, and configs

🔹 Basic Concepts ⭐

Inventory → list of servers

Playbook → automation file (YAML)

Task → single action

Module → unit of work

🔹 Inventory File Example

\[web\]

192.168.1.10

192.168.1.11

🔹 Basic Commands

ansible all -m ping

ansible all -a "uptime"

ansible web -m apt -a "name=nginx state=present"

🔧 Common Modules + Important Arguments ⭐

📦 apt (Package Management)

\- name: Install nginx

apt:

name: nginx

state: present

update\_cache: yes

⚙️ service (Manage Services)

\- name: Start nginx

service:

name: nginx

state: started

enabled: yes

📁 copy (Copy Files)

\- name: Copy index file

copy:

src: index.html

dest: /var/www/html/index.html

owner: root

mode: '0644'

📂 file (Manage Files/Dirs)

\- name: Create directory

file:

path: /var/www/html

state: directory

mode: '0755'

👤 user (User Management)

\- name: Create user

user:

name: devops

state: present

groups: sudo

🌐 get\_url (Download Files)

\- name: Download file

get\_url:

url: https://example.com/app.tar.gz

dest: /tmp/app.tar.gz

▶️ Playbook Execution

ansible-playbook playbook.yml

📄 Sample Playbook ⭐

\- name: Install Nginx

hosts: web

become: yes

tasks:

\- name: Install package

apt:

name: nginx

state: present

update\_cache: yes

\- name: Start service

service:

name: nginx

state: started

enabled: yes