restart-webapplication
======================

Generic role to restart a web application. It then waits for the port, and test a page.

Requirements
------------

This role requires Ansible 1.4 or higher, and platform requirements are listed in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	# service to restart
	service_name: httpd

	# process name to wait
	process_name:
	# if kill_process=true, will kill all the processes
	kill_process: false
	# check the process recursively till it die or the task has been retried for 12 times with a delay of 5 seconds
	process_retries: 12
	process_delay: 5

	# which port to check
	service_port: 80
	# how long to wait for service_port to be up
	service_port_timeout: 60

	# which page to check, pass blank to homepage if no checking is required.
	homepage: http://localhost:{{service_port}}
	# check the homepage recursively till it return status 200 or the task has been retried for 12 times with a delay of 5 seconds
	homepage_retries: 12
	homepage_delay: 5



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
