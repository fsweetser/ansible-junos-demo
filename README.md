DESCRIPTION
===========

Ansible demo to "kickstart" Junos network infrastructure.  The `deploy.yml` playbook will perform
the following actions:

1.  Check to see if the device is reachable via NETCONF
2.  Install the correct version of the Junos OS software
3.  Reboot the device and wait for restart if the OS was changed
4.  Template build an initial configuration
5.  Install the initial configuration on the device

SETUP
=====

You will need to first git clone the [ansible-junos-stdlib](https://github.com/jeremyschulman/ansible-junos-stdlib) repository.  

Then `source env-setup` to propertly setup your environment for ansible-playbook.

Then create /usr/local/junos/{log,configs,packages}.  Put your Junos OS images (*.tgz) in the packages directory.  

Copy the `catalog.yml` to /usr/local/junos/packages.  You can then setup your own image tag names, etc.


