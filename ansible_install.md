# Setting Up and Running an Ansible Playbook to Install Apache on EC2


### Step 1: Install Ansible
```bash
yum install -y ansible
```

### Step 2: Verify Ansible Installation
```bash
ansible --version
```

### Step 3: Create a Directory for Ansible Files
```bash
mkdir ansible
```

### Step 4: Navigate to the Ansible Directory
```bash
cd ansible
```

### Step 5: Create an Ansible Playbook File
```bash
touch playbook.yml
```

### Step 6: Add the Following Configuration to `playbook.yml`
```bash
- name: Install and configure web server
  hosts: localhost
  connection: local
  become: true
  tasks:
    - name: Install Apache web server
      ansible.builtin.package:
        name: "{{ ''apache2'' if ansible_os_family == ''Debian'' else ''httpd'' }}"
        state: present

    - name: Create index.html file
      ansible.builtin.template:
        src: index.html.j2
        dest: "{{ ''/var/www/html/index.html'' if ansible_os_family == ''Debian'' else ''/var/www/html/index.html'' }}"

    - name: Set ownership and permissions on index.html
      ansible.builtin.file:
        path: "{{ ''/var/www/html/index.html'' if ansible_os_family == ''Debian'' else ''/var/www/html/index.html'' }}"
        owner: "{{ ''www-data'' if ansible_os_family == ''Debian'' else ''apache'' }}"
        group: "{{ ''www-data'' if ansible_os_family == ''Debian'' else ''apache'' }}"
        mode: "0644"

  handlers:
    - name: restart apache
      ansible.builtin.service:
        name: "{{ ''apache2'' if ansible_os_family == ''Debian'' else ''httpd'' }}"
        state: restarted
```

### Step 7: Create a Template File for the Web Page
```bash
touch index.html.j2
```

### Step 8: Add the Following HTML Content to `index.html.j2`
```bash
echo '<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ansible</title>
</head>
<body>
    <h1>Hello World!</h1>
</body>
</html>' > index.html.j2
```


### Step 9: Run the Ansible Playbook
```bash
ansible-playbook playbook.yml
```

### Step 10: Open the Public IP of the EC2 Instance in the Browser to See the Output
