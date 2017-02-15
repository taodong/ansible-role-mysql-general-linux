Ansible Role: MySQL Role for Amazon Linux or Generic Linux
=========

Installs MySQL 5.7.17 community server on Amazon Linux/Generic Linux servers

Requirements
------------

This role requires root access.

Role Variables
--------------

Available variables are listed below, along with default values:

```
mysql_bin_dir: /home/ec2-user
```
A folder to save MySQL binary installer file

```
mysql_bin_file: mysql-5.7.17-linux-glibc2.5-x86_64.tar.gz
```
MySQL binary installer file name, should be a general Linus installer available on MySQL repository http://dev.mysql.com

```
mysql_install_dir: /usr/local
```
Parent directory to create MySQL home

```
mysql_home_dir: "{{ mysql_bin_file | regex_replace('\\.tar|\\.gz', '')}}"
```
MySQL home directory name. Default will be the same as the binary installer file name without tar and gz. The installer will create a soft link mysql points to this real directory

```
mysql_admin_user: root
```
MySQL admin user name

```
install_output_dir: /home/ec2-user 
```
Directory to save installation output file. The output file will be db_rs.txt which contains temporary root passowrd

Dependencies
------------

None

Example Playbook for Amazon Linux
----------------

```
- hosts: all
  remote_user: "ec2-user"
  become: yes
  become_method: sudo

  roles:
    - taodong.mysql-general-linux
```

License
-------

MIT

Author Information
------------------

This role was created in 2017 by Tao Dong
