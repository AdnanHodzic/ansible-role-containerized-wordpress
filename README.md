Ansible Role: Containerized WordPress
=========

This Ansible playbook will Deploy & run Docker Compose project for WordPress instance. Which consists of 3 separate containers running:
* WordPress (PHP7 FPM)
* Nginx
* MariaDB

Requirements
------------

For this role to work, it is required to have have Docker and Docker Compose installed and setup. If you haven't done this already (manually), then you're required to install following role: [AdnanHodzic.docker-compose-setup](https://galaxy.ansible.com/AdnanHodzic/docker-compose-setup/).

Role Variables
--------------

This role comes with following variables defined in defaults/main.yml:

```
system_user: ubuntu
compose_project_dir: /home/{{ system_user }}/compose-wordpress
domain: foolcontrol.org
wp_version: 4.7.5
wp_db_name: wordpress
wp_db_tb_pre: wp_
wp_db_host: mysql
wp_db_psw: change-M3
```

If role is run without changing these, WordPress instance with Nginx virtual host as well as Database settings will be setup with these values. 

**ToDo:** 
Add full link to where these are explained on http://foolcontrol.org/?p=2002 post


Dependencies
------------

**ToDo:**
Determine if "AdnanHodzic.docker-compose-setup" role should be set as role dependency. If yes, update this section of ReadMe + meta code.

Example Playbook
----------------

```
- hosts: servers
  remote_user: "{{ system_user }}"
  roles:
    - { role: AdnanHodzic.containerized-wordpress }}  
```

License
-------

GPLv3
