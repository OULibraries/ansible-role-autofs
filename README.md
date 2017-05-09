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
  - mount_point: /mnt/autofs
    mount_name: somename1
    maps:
      - map_key: share1
        map_options:
          - name: fstype
            options: ['nfs','rw']
        map_location:
            host: 192.168.1.9
            path: :/srv/share1
  - mount_point: /-
    mount_name: somename2
    maps:
      - map_key: /srv
        map_options:
          - name: fstype
            options: ['nfs','ro']
          - name: context
            options: ['system_u:object_r:httpd_sys_content_t:s0']
        map_location:
            host: 192.168.1.9
            path: :/srv/share2
  - mount_point: '/mnt/autofs/smb'
    mount_name: 'smb'
    maps:
      - map_key: 'share3'
        map_options:
          - name: 'fstype'
            options: ['cifs','rw','noperm','sec=ntlm','credentials=/root/.smbcredentials']
          - name: 'uid'
            options: ['0']
          - name: 'gid'
            options: ['0']
          - name: 'dir_mode'
            options: ['0775']
          - name: 'file_mode'
            options: ['0664']
        map_location:
            host: '://192.168.1.9'
            path: '/share3'
      - map_key: 'share4-deep'
        map_options:
          - name: 'fstype'
            options: ['cifs','rw','noperm','sec=ntlm','credentials=/root/.smbcredentials']
          - name: 'uid'
            options: ['0']
          - name: 'gid'
            options: ['0']
          - name: 'dir_mode'
            options: ['0775']
          - name: 'file_mode'
            options: ['0664']
        map_location:
            host: '://192.168.1.9'
            path: '/share4/deep'

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
