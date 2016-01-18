Role Name
=========

Installs haproxy http://www.haproxy.org/

Requirements
------------

None...unless using GlusterFS

Role Variables
--------------

````
---
# defaults file for ansible-haproxy
config_haproxy: false #only set to true to actually configure a base HAProxy config which is already installed by default
debian_haproxy_repo: ppa:vbernat/haproxy-1.5
enable_haproxy_admin_page: true
enable_haproxy_remote_syslog: false  #defines if logs should be sent to remote syslog server
haproxy_admin_password: admin  #defines password for admin user to login to admin page
haproxy_admin_port: 9090  #defines http port to listen on for admin page
haproxy_admin_user: admin  #defines admin user to login to admin page
haproxy_backup_dir: /etc/haproxy.backup  #defines location to backup haproxy to when using with GlusterFS
haproxy_docker_install: false  #defines if haproxy is being installed in Docker
haproxy_home: /etc/haproxy  #defines haproxy default location
haproxy_mnt: ''  #define if using GlusterFS
pri_domain_name: example.org
primary_gfs_server: ''  #define if using GlusterFS
secondary_gfs_server: ''  #define if using GlusterFS
sync_haproxy: false  #this is only needed when using GlusterFS
syslog_servers:
  - name: 'logstash.{{ pri_domain_name }}'
    proto: tcp
    port: 514
````

Dependencies
------------

None...unless using GlusterFS

Example Playbook
----------------

#### GitHub
````
- hosts: all
  remote_user: remote
  become: true
  vars:
  roles:
    - role: ansible-haproxy
  tasks:
````
#### Galaxy
````
- hosts: all
  remote_user: remote
  become: true
  vars:
  roles:
    - role: mrlesmithjr.haproxy
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
