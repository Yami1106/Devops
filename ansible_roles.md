### Steps to Create and Run an Ansible Role with Playbook

### Step0: complete ansible_install.md first

### Step 1 **Navigate to the Ansible directory:**

```bash
   cd /etc/ansible
```

### Step 2 create a role using :

```bash 
ansible-galaxy admin
```

### Step 3: move into tasks

```bash
cd admin/tasks
```

### Step4: edit the main.yml file and enter this :

```
# roles/admin/tasks/main.yml
---
- name: Print Hello World
  command: echo "Hello World"
```

### Step 5: mode to playbook.yml and paste this

```
- name: Install and configure web server
  hosts: localhost
  connection: local
  become: true
  roles:
    - /etc/ansible/admin
  tasks:
    - name: Install Apache web server
      ansible.builtin.package:
        name: "{{ 'apache2' if ansible_os_family == 'Debian' else 'httpd' }}"
        state: present

    - name: Create index.html file
      ansible.builtin.template:
        src: index.html.j2
        dest: "{{ '/var/www/html/index.html' if ansible_os_family == 'Debian' else '/var/www/html/index.html' }}"

    - name: Set ownership and permissions on index.html
      ansible.builtin.file:
        path: "{{ '/var/www/html/index.html' if ansible_os_family == 'Debian' else '/var/www/html/index.html' }}"
        owner: "{{ 'www-data' if ansible_os_family == 'Debian' else 'apache' }}"
        group: "{{ 'www-data' if ansible_os_family == 'Debian' else 'apache' }}"
        mode: "0644"

  handlers:
    - name: restart apache
      ansible.builtin.service:
        name: "{{ 'apache2' if ansible_os_family == 'Debian' else 'httpd' }}"
        state: restarted
```

### Step 6: run playbook 

```bash
ansible-playbook playbook.yml
```




