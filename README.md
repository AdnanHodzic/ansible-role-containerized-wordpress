Ansible Role: Containerized WordPress
=========

This Ansible playbook will Deploy & run Docker Compose project for WordPress instance. It will also configure Let's Encrypt certificates for specified domain. It consists of 3 separate containers running:
* WordPress
* Nginx (enabled with Let's Encrypt HTTPS encryption)
* MySQL

This role was created as part of [containerized-wordpress-project](https://github.com/AdnanHodzic/containerized-wordpress-project)

Requirements
------------

For this role to work, it is required to have have Docker and Docker Compose installed and setup. If you haven't done this already (manually), then you're required to install following role: [AdnanHodzic.docker-compose](https://galaxy.ansible.com/AdnanHodzic/docker-compose).

Role Variables
--------------

This role comes with following variables defined in defaults/main.yml:

```
system_user: ubuntu
compose_project_dir: /home/{{ system_user }}/compose-wordpress
domain: foolcontrol.org
stage: staging
wp_version: 5.2.4
wp_db_user: admin
wp_db_psw: change-M3
db_root_psw: change-M3
wp_db_name: wordpress
wp_db_tb_pre: wp_
wp_db_host: mysql
```

If role is run without changing these, WordPress instance with Nginx virtual host as well as Database settings will be setup with these values. 

`stage` is an important value and its detailed explanation can be found on: [Let's Encrypt certificates (HTTPS encryption)](https://github.com/AdnanHodzic/containerized-wordpress-project/blob/master/README.md#5-lets-encrypt-certificates-https-encryption)

Blog post discussion: 
* [Automated way of getting Let’s Encrypt certificates for WordPress using Docker + Ansible](http://foolcontrol.org/?p=2758)
* [Automagically deploy & run containerized WordPress (PHP7 FPM, Nginx, MariaDB) using Ansible + Docker on AWS](http://foolcontrol.org/?p=2002)


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

Donate
-------

Since I'm working on this project in free time, please consider supporting this project by making a donation of any amount!

##### PayPal
[![paypal](https://www.paypalobjects.com/en_US/NL/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=7AHCP5PU95S4Y&item_name=Contribution+for+work+on+containerized-wordpress-project&currency_code=EUR&source=url)

##### BitCoin
[bc1qlncmgdjyqy8pe4gad4k2s6xtyr8f2r3ehrnl87](bitcoin:bc1qlncmgdjyqy8pe4gad4k2s6xtyr8f2r3ehrnl87)

[![bitcoin](https://foolcontrol.org/wp-content/uploads/2019/08/btc-donate-displaylink-debian.png)](bitcoin:bc1qlncmgdjyqy8pe4gad4k2s6xtyr8f2r3ehrnl87)
