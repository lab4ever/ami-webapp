Role NGINX
=========

Instalaçao do nginx, configuraçoes definidas por variaveis. O intuito e gerar templates para diferentes tipos de web servers

Requirements
------------
- Role tem que ser instalada pelo bitbucket nashbit

Role Variables
--------------
```yaml
nginx_state: present

server_hostname: "site_name"

worker_connections: 4000
worker_rlimit_nofile: 100000

access_log: "/var/log/nginx/access.log"
error_log: "/var/log/nginx/error.log"

keepalive_timeout: 30
keepalive_requests: 100000

enable_web_server_php: "false"
php_fpm_version: "7.2"
```

Dependencies
------------


Example Playbook
----------------
```yaml
- hosts: all
  become: yes
  vars:
    - server_hostname: "www.example.com"

  pre_tasks:
   - name: install the required package
     apt:
      name: ['ansible','python3-pip']
      state: present
      update_cache: yes

  roles:
    - role-nginx
```

Author Information
------------------
Ramon Salado
