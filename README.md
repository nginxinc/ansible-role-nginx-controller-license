NGINX Controller License
========================

A role to push an NGINX Controller license to your NGINX Controller platform.

Requirements
------------

*   [NGINX Controller](https://www.nginx.com/products/nginx-controller/)
*   NGINX Controller license file

Role Variables
--------------

`license` - A base64 encoded string of your NGINX Controller license file.

`controller_fqdn` - The FQDN / hostname of your Controller server.

`controller_auth_token` - Authentication token for NGINX Controller. You can use the `nginxinc.nginx-controller-generate-token` role to set this variable.

Dependencies
------------

none

Example Playbook
----------------

```yaml
- hosts: localhost
  gather_facts: no

  vars:
    controller_fqdn: controller.mydomain.com
    # NGINX Controller license role vars
    # base64 encoded, one line, no line endings or carriage returns
    license: "{{ lookup('file', 'license/controller_license.base64.txt') }}"
    # Only required if NGINX Controller generate token role is not used
    # controller_auth_token: <token>
    # NGINX Controller generate token role vars
    user_email: user@example.com
    user_password: mySecurePassword

  tasks:
    - include_role:
        name: nginxinc.nginx-controller-generate-token

    - include_role:
        name: nginxinc.nginx-controller-license
```

License
-------

[Apache License, Version 2.0](./LICENSE)

Author Information
------------------

brianehlert
