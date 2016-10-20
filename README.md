Role Name
=========

Generic role to restart a web application. It then waits for the port, and test a page.

Requirements
------------

This role requires Ansible 1.4 or higher, and platform requirements are listed in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	service_name: httpd
	service_port: 80
	homepage: http://localhost:{{service_port}}


Dependencies
------------

None

Example Playbook
----------------

Restart the default web application (httpd):

    - hosts: servers
      roles:
        - quekky.restart-webapplication

Restart the tomcat, which is running on port 8080, then test the page http://localhost:8080/test.jsp:

    - hosts: servers
      roles:
         - role: quekky.restart-webapplication
		   service_name: tomcat8
		   service_port: 8080
		   homepage: http://localhost:8080/test.jsp

License
-------

MIT

Author Information
------------------

quekky
