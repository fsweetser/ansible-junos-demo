DESCRIPTION
===========

Ansible demo to "kickstart" Junos network infrastructure.  The `deploy.yml` playbook will perform
the following actions:

1.  Check to see if the device is reachable via NETCONF
2.  Install the correct version of the Junos OS software
3.  Reboot the device and wait for restart if the OS was changed
4.  Template build an initial configuration
5.  Install the initial configuration on the device

Please note this is very early stage work, but many folks have asked me to share it asap.  I'll be working
on this to fix up hardcoded barnacles asap.  


SETUP
=====

You will need to first git clone the [ansible-junos-stdlib](https://github.com/jeremyschulman/ansible-junos-stdlib) repository.  

Then `source env-setup` to propertly setup your environment for ansible-playbook.  You may need to CHANGE the env-setp file so it points to your ANSIBLE installation.  I've got mine set to `$HOME/ansible`.

Then create /usr/local/junos/{log,configs,packages}.  Put your Junos OS images (*.tgz) in the packages directory.  

Copy the `catalog.yml` to /usr/local/junos/packages.  You can then setup your own package tag names, etc.  You then associate the package name to the Junos devices in the `hosts` file.

The sample playbooks/tasks do not include using the user/password arguments.  If you want to use these "as-is" you will need make sure you've got ssh-keys installed on your Junos devices.  Otherwise, youw will need to modify the playbooks to use user/password args.

# USAGE

## Audit Junos OS images

````
$ ansible-playbook junos/audit_os.yml -i hosts
````

## Retrieve the Junos "facts"
````
$ ansible-playbook junos/get_junos_facts.yml -i hosts -v
````

## Run the full Deployment
````
$ ansible-playbook deploy.yml -i hosts
````

LICENSE
=======
BSD-2

AUTHORS
=======
* Jeremy Schulman, @nwkautomanic

Special thanks to the folks at [AnsibleWorks](http://www.ansibleworks.com) for all thier help!

