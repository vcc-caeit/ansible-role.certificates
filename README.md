certificates
============

Ansible role to copy certificates to a system with resonable defaults.

Role Variables
--------------

This role only supports one variable, `certificates`. By default this is an empty list. You can specify `src`, `dest`, `data`, `owner`, `group`, `mode`.

    certificates:
      - src: which file to copy to the server
        data: content to copy to the server
        dest: file on the server to populate
        owner: file owner, defaults to 'root'
        group: file group, defaults to 'root'
        mode: file access, defaults to 0640 if 'private' is in `dest` and 0644 otherwise.

Example Playbook
----------------

    - hosts: servers
      vars:
        certificates:
          - src: certs/example.pem
            dest: /etc/ssl/certs/example.pem
          - data: "{{ lookup('url', 'https://www.cisco.com/security/pki/certs/ciscoumbrellaroot.pem', split_lines=False)
            dest: /etc/ssl/certs/ciscoumbrella.pem
      roles:
         - vcc_caeit.certificates

License
-------

GPLv2

Author Information
------------------

This role was created in 2022 by Nafallo Bjälevik, whilst doing consultancy work for [Volvo Cars](http://www.volvocars.com/).
