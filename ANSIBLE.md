Ansible for SMTF
=====
The shipped ansible code provides several tasks to be accomplished:
- generate a Vagrantfile including the "physical" networking
- populate hostname.if(5) based on group/host_vars

Vagrantfile
-----
The following commands generates a Vagrantfile based on group_vars/rdomain.yml information
and bring up the testbed including the base network (vboxnets).
````
$ ansible-playbook -i local_inventory -e 'rdomain=true' vagrant-pb.yml
$ vagrant up
````

hostname.if(5)
-----
With the following playbook ansible will generate /etc/hostname.X files to match the above Vagrantfile.
Also some needed sysctl.conf will be written/activated and a bit of ksh profile tweaking (PS1 for now).
````
$ ansible-playbook -i vagrant_inventory rdomain-pb.yml
````
