Hi, ![](https://user-images.githubusercontent.com/18350557/176309783-0785949b-9127-417c-8b55-ab5a4333674e.gif)my name is Serhii Shypylov
=========================================================================================================================================

💛 I am a Linux System administrator engineer with DevOps practices. I have several certificates in Linux, Docker, Ansible and Terraform and continue to learn more. I like everything related to Docker, containers and IT technologies in general. I love solving complex IT solutions.
-------------------------------

* 💼 Looking for a job
* 🌍 I'm based in Poznan
* 🖥️ See my [LinkedIn](https://github.com/Shipssv83) profile 
* 👾 Chat with IT pros on [Discord](https://discord.com/shipssv_19055)\
* 📧 Reach me at ships@ukr.net
* 🧠 I'm learning DevOps Practices

### Socials

<p align="left"> <a href="https://github.com/Shipssv83" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" width="32" height="32" /> </picture> </a> <a href="https://www.linkedin.com/in/sergey-shipilov-7262a31b4/" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" width="32" height="32" /> </picture> </a></p>

# Nginx Proxy Manager Docker Installation via Ansible

This project contains Ansible playbooks for setting up a server, installing Docker, and deploying the Nginx Proxy Manager (PM) in a Docker container. It also configures UFW firewall rules for web access and Nginx.

## Overview

The playbooks cover the following installation steps:
1. **Server Setup**: Configures the server's basic settings such as timezone.
2. **Docker Installation**: Installs Docker and Docker Compose.
3. **Nginx Proxy Manager Installation**: Deploys Nginx PM inside a Docker container, setting up database and web server access.

## Playbooks Overview

### 1. Server Installation (`server-install.yml`)

This playbook handles the setup of essential system configurations and packages.

### 2. Docker Installation (`docker-install.yml`)

This playbook installs Docker and Docker Compose, making the server ready for containerized applications.

### 3. Nginx Proxy Manager Installation (`nginx-pm-docker-install.yml`)

This playbook installs and configures Nginx Proxy Manager (PM) inside a Docker container. It sets up database credentials, configures the web interface, and allows access through UFW firewall.

## Variables

The following variables can be configured for the installation:

- `email`: Email address for Nginx Proxy Manager admin account.
- `nginx_mysql_pass_web`: Password for accessing the MySQL database from the web interface (default: `changeme`).
- `nginx_pm_host_name`: Hostname for the Nginx Proxy Manager instance.
- `nginx_mysql_user`: MySQL username.
- `nginx_mysql_pass`: MySQL password for the Nginx Proxy Manager database.
- `nginx_mysql_name`: Name of the MySQL database for Nginx Proxy Manager.
- `nginx_mysql_root_pass`: MySQL root password.
- `your_ip`: The IP address to allow through UFW for access to the Nginx port.

### Example Configuration

```yaml
vars:
  email: 'admin@example.com'
  nginx_mysql_pass_web: 'changeme'
  nginx_pm_host_name: 'host_name'
  nginx_mysql_user: 'your_user_name'
  nginx_mysql_pass: 'complex_password'
  nginx_mysql_name: 'your_user_name'
  nginx_mysql_root_pass: 'complex_password'
  your_ip: '19.16.11.12'

```

# ansible galaxy roles

```
### install role ansible galaxy
ansible-galaxy install -r roles/requirements.yml

### upgrade role ansible galaxy 
ansible-galaxy install -g -f -r roles/requirements.yml
```

# Run the Playbook install
Run the playbook by specifying your inventory file and variable file:

```
ansible-playbook -i inventory --user root --extra-vars "host=host_name" playbooks/nginx-pm-docker-install.yml
```
Accessing Nginx Proxy Manager
Once installation is complete, you can access the Nginx Proxy Manager via the web interface using the following credentials:

Email: admin@example.com
Password: changeme
You can log in to Nginx Proxy Manager at:
```
http://<your-server-ip>:81
```
After the first login, it is highly recommended to change the default password.

Conclusion
This project simplifies the deployment of Nginx Proxy Manager using Docker and Ansible, with UFW firewall rules to secure the setup.

This **README** explains the playbooks and variables required for installing Nginx Proxy Manager with Docker and configuring firewall rules for secure web access.

License
This project is licensed under the MIT License