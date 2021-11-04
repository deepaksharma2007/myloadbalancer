myloadbalancer
=========

This role is used to configure haproxy load balancer . Also this role solving challenge for *host ip’s addition dynamically* over each Managed Node in HAProxy.cfg file.


Requirements
------------
🔆 Ansible must be configured well in your controller node

🔆 We must have connectivity between controller node and Managed node. You can check by command (ansible webservers -m ping) .

🔆 Also make host name of servers in inventory file must be "webservers". Add all servers under "webservers" host to configure apache webservers.

🔆 This role is applied after myapache role. otherwise it will be failed .Because loadbalancer does not get any running webserver.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. I used basically two variable
1. pkgs: This is used to tell which software will be install.
2. rule: This is used to create firewall rule . So we can access http and https services.

Dependencies
------------

🔆 This role is dependent on myapache role(https://galaxy.ansible.com/deepaksharma2007/myapache). myapache role configure webserver and then myloadblancer register these webservers to load balancer. So we can directly access content of webserver by loadbalancer.

🔆 myloadbalancer is solving challenge for *host ip’s addition dynamically* over each Managed Node in HAProxy.cfg file. For this in inventory file all webserver managed node are under "webservers" host group.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: lb
      roles:
         - { role: path }
         
      here path= where you downloaded myloadbalancer

License
-------

BSD

Author Information
------------------
The author of this role is Deepak Sharma
