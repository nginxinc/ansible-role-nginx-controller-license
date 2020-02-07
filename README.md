Role Name
=========

A brief description of the role goes here.

Requirements
------------

NGINX Controller
NGINX Controller license file

Role Variables
--------------

base64 encoded string of your Controller license file
license: ""

Authentication token for Controller
controller_auth_token: ""

The FQDN / hostname of your Controller server
controller_fqdn: ""

Dependencies
------------

none

Example Playbook
----------------

# ansible-playbook nginx_controller_license.yaml -i controller -e "admin_email=user@company.com admin_password=userPassword" 
# ansible-playbook nginx_controller_license.yaml -e "@nginx_install_controller_vars.yaml"

- hosts: localhost
  gather_facts: no

  vars:
    # base64 encoded, one line, no line endings or carrage returns
    license: "{{ lookup('file', 'license/controller_license.base64.txt') }}"

  tasks:
  - include_role:
      name: ansible-role-nginx-controller-generate-token

  - include_role:
      name: ansible-role-nginx-controller-license

License
-------

Apache

Author Information
------------------

BrianEhlert
