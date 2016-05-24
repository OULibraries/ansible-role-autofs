OULibraries.autofs
=========

AutoFS for OULib.

Requirements
------------

A target system running CentOS7x.

Role Variables
--------------

```
autofs:
  - mount_point: /mnt
    - key: share1
      options: ['-fstype=nfs','rw']
      location:
        ip: 192.168.1.9
        path: /srv/share1
  - mount_point: /-
    - key: /srv
      options:
        - key: fstype
          value: ['nfs','ro']
          key: context
          value: ['system_u:object_r:httpd_sys_content_t:s0']
      location:
        ip: 192.168.1.9
        path: /srv/share2
```
and so forth. See defaults/mail.yml for any other vars.

Dependencies
------------


Example Playbook
----------------


License
-------

TBD

Author Information
------------------

Jason Sherman
