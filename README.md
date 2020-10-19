Apache Tomcat with Manager GUI
==============================

[![Travis](https://img.shields.io/travis/honatas/ansible-role-tomcat-dev?style=plastic)](https://travis-ci.org/Honatas/ansible-role-tomcat-dev "View the build status on Travis")
[![coffee](https://img.shields.io/badge/buy%20me%20a-coffee-orange?style=plastic)](https://ko-fi.com/honatas "Buy me a coffee")


Ansible role for installing Apache Tomcat as a systemd service with the Manager GUI enabled. Remote access to the GUI is allowed, so this role is not recommended for production environments.


Requirements
------------

Tomcat needs a Java installation in order to run. Since there are a number of ways to do it, this was not added as a dependency to this role, so you have more freedom of choice. Therefore, you must ensure you have Java installed prior to running this role. If you allow me, I can suggest the [openjdk-ppa](https://galaxy.ansible.com/honatas/openjdk_ppa) role for that purpose.


Role Variables
--------------

**tomcat_version**: The version you want installed.  
default: 9.0.34  

**tomcat_linux_user**: The username under which Tomcat will run.  
default: vagrant

**tomcat_install_dir**: Installation folder.  
default: /home/{{ tomcat_linux_user }}  (which translates to /home/vagrant)  

**tomcat_manager_gui_username**: Username of the Manager GUI  
default: admin  

**tomcat_manager_gui_password**: Password of the Manager GUI  
default: admin  


Example Playbooks
-----------------

Default installation
```yaml
roles:
  - honatas.tomcat_dev
```

With Java
```yaml
roles:
  - honatas.openjdk_ppa
  - honatas.tomcat_dev
```

Another version
```yaml
roles:
  - { role: honatas.tomcat_dev, tomcat_version: 9.0.20 }
```

Another user and a different folder (make sure the folder is created and the user has permission)
```yaml
roles:
  - role: honatas.tomcat_dev
    tomcat_linux_user: myuser
    tomcat_install_dir: /opt
```

Dependencies
------------

None.


License
-------

MIT
