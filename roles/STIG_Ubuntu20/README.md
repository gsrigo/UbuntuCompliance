NIST800-171_Ubuntu20
=========

This role attempts to bring an Ubuntu 20.04 to a high compliance level with NIST 800-171 (DFARS)

Requirements
------------

None.

Role Variables
--------------

All variables are defined on vars/main.yml.

Dependencies
------------

None.

Example Playbook
----------------

- name: DFARS and Post-Provisioning Ansible Job
  hosts: all
  become: yes

  roles:
    - role: NIST800-171_Ubuntu20
      tags:
        - NIST800_171

License
-------

MIT

Author Information
------------------

This code is part of a Graduate Project Class at UMD ENPM697 along with professional 
need for NIST 800-171 for Ubuntu machines at my workplace.