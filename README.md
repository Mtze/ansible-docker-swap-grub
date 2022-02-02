Role Name
=========

This role fixes the 
```
WARNING: No swap limit support
```
warning in `docker info` by reconfiguring `grub`. 


The [docker documentation](https://docs.docker.com/config/containers/resource_constraints/) mentions this issue and [describes how to solve it by reconfiguring grub](https://docs.docker.com/engine/install/linux-postinstall/#your-kernel-does-not-support-cgroup-swap-limit-capabilities).  


TLDR: 

This role updates `/etc/defaults/grub` to inclunde 
```
GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"
```

Requirements
------------

None

Role Variables
--------------

See [`defaults/main.yml`](defaults/main.yml). 

Dependencies
------------

None

Example Playbook
----------------

### Update grub and reboot
```
- hosts: docker_hosts
  roles:
     - role: mtze.docker-swap-grub
       vars: 
```
### Update grub and prevent reboot
```
- hosts: docker_hosts
  roles:
     - role: mtze.docker-swap-grub
       vars: 
         allow_reboot: false
```

License
-------

MIT

