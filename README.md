NGINX Controller License
========================

A role to push an NGINX Controller license to your NGINX Controller platform.

Requirements
------------

*   [NGINX Controller](https://www.nginx.com/products/nginx-controller/)
*   [NGINX Controller](https://www.nginx.com/products/nginx-controller/) license file

Role Variables
--------------

-- All the below variables are required --

`nginx_controller_license` - A base64 encoded string of your NGINX Controller license file. Has to be one line, with no line endings or carriage returns. The below example uses the b64encode filter to do this encoding. 

`nginx_controller_fqdn` - The FQDN / hostname of your Controller server.

`nginx_controller_auth_token` - Authentication token for NGINX Controller. You can use the `nginxinc.nginx_controller_generate_token` role to set this variable.

Dependencies
------------

none

Example Playbook
----------------

To use this role you can create a playbook such as the following:

```yaml
- hosts: localhost
  gather_facts: no

  vars:
    nginx_controller_user_email: "user@example.com"
    nginx_controller_user_password: "mySecurePassword"
    nginx_controller_fqdn: "controller.mydomain.com"
    nginx_controller_validate_certs: false

  tasks:
    - name: Retrieve the NGINX Controller auth token
      include_role:
        name: nginxinc.nginx_controller_generate_token

    - name: Push the NGINX Controller license to your instance
      include_role:
        name: nginxinc.nginx_controller_license
      vars:
        # controller.auth_token: output by previous role in example
        nginx_controller_license: "{{ lookup('file', 'license/controller_license.txt') | b64encode }}"
```

License
-------

[Apache License, Version 2.0](./LICENSE)

Author Information
------------------

[Brian Ehlert](https://github.com/brianehlert)

[Alessandro Fael Garcia](https://github.com/alessfg)

[Daniel Edgar](https://github.com/aknot242)

&copy; [NGINX, Inc.](https://www.nginx.com/) 2020
