Ansible AWS Windows
===================

Ansible EC2 Demo

Uses Ansible to launch a Windows AMI in AWS and configure it to allow
management by Ansible over WinRM.

The second role configures a web application called ping.

Ansible Tower
- Create an Inventory
  - The only host that should exist is localhost with a variable 'ansible_connection: local'
  - Create a group called 'windows' the variables for that group should be:

ansible_port: 5986
ansible_connection: winrm
ansible_winrm_server_cert_validation: ignore

- Create Template
  - The template should have a survey with the following variables (with example values)

aws_region: us-east-2
iis_roles_features: Web-WebServer,Web-Common-Http,Web-Static-Content,Web-Default-Doc,Web-Http-Errors,Web-Http-Redirect,Web-ASP,Web-Http-Logging,AS-Web-Support
ami_name: Windows_Server-2012-R2_RTM-English-64Bit-Base-*
instance_type: t2.micro
ansible_user: Administrator
ansible_password: <password>
aws_access_key_id: <aws_access_key>
aws_secret_access_key: <aws_secret_key>

