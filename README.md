ansible-role-wordpress-nginx
=========

Ansible Role to install worpress server and nginx with ssl certificate, generated by letsencrypt.

## Table of Contents
- [Role Variables](#Role-Variables)
  * [General Parameters](#General-Parameters)
  * [MariaDB Parameters](#MariaDB-Parameters)
  * [Let'sencrypt Parameters](#Let'sencrypt-Parameters)
  * [Wordpress Parameters](#Wordpress-parameters)
- [Example Playbook](#Example-Playbook)
- [License](#License)
- [Author Information](#Author-Information)

Role Variables
--------------
Variables are located in [deafults/main.yml](defaults/main.yml) file.

### General Parameters ###

- **hostname** --> Full name of the DNS pointed to the Machine IP (server.my.domain).
- **domain** --> The domain if the DNS of the server.
- **hostname_no_fqdn** --> The name of the server without the domain ending.
- **install_nginx** --> Set true to install nginx (must be **true** for first installation).
- **install_mariadb** --> Set true to install mariaDB (must be **true** for first installation).
- **install_php** --> Set true to install php (must be **true** for first installation).
- **install_wordpress** --> --> Set true to install wordpress (must be **true** for first installation).
- **add_host** --> Set true when you are adding host to exist installation.

```bash
## General parameters
hostname: webserver.domain.com
domain: domain.com
hostname_no_fqdn: webserver
install_nginx: false
install_mariadb: false
install_php: false
install_wordpress: true # true when creating new host
add_host: true # Set true when you are adding host to exist installation

```

### MariaDB parameters ###

**mysql_root_password** --> Root Password for mariaDB.

```bash
## MariaDB parameters
mysql_root_password: 'Aa123456'
```


### letsencrypt parameters ###

**certbot_admin_email** --> Email Address for letsencrypt certificate generation.

```bash
## letsencrypt parameters
certbot_admin_email: yourmail@mail.com
```

### Wordpress parameters ###

- **wordpress_path** --> Enter the path for wordpress '/blog' or '/wp' or '/' for example.
- **wp_db_name** --> Wordpress db name.
- **wp_db_name** --> Wordpress Database name.
- **wp_db_user** --> Wordpress Database user.
- **wp_db_password** --> Wordpress Database user password.
- **table_prefix** --> Wordpress DB table prefix
- **admin_user** --> Admin user for wordpress.
- **admin_password** --> Admin password for wordpress.
- **title** --> Title for the site (title without spaces!).

```bash
## Wordpress parameters
wordpress_path: '/blog' # Enter the path for wordpress '/blog' or '/wp' or '/' for example.
wp_db_name: wpdb_{{ hostname_no_fqdn }}
wp_db_user: wpdbuser
wp_db_password: 'Aa123456'
table_prefix: wp_
admin_user: gal
admin_password: Aa123456
admin_email: youreamail@mail.com
title: gal10
```

Example Playbook
----------------
Before you run fill the paraneters in [deafults/main.yml](defaults/main.yml), **OR** set vars section in the playbook file:

```bash
- hosts: servers
  become: yes
  vars:
    - var1
    - var2
  roles:
    - ansible-role-wordpress-nginx
```
Every variable that will not entered above, his value will be taken from the defaults file.

Playbook after filling [deafults/main.yml](defaults/main.yml).

    - hosts: servers
      become: yes
      roles:
         - ansible-role-wordpress-nginx

License
-------

BSD

Author Information
------------------

<b>Gal Birkman, DevOps Engineer.</b><br>
<b>email:</b> galbirkman@gmail.com<br>
<b>GitHub:</b> https://github.com/galbirk
