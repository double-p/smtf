Ansible for SMTF
=====
The shipped ansible code provides several tasks to be accomplished:
- generate a Vagrantfile including the "physical" networking

Vagrantfile
-----
The following command generates a Vagrantfile based on group_vars/rdomain.yml information
````
ansible-playbook -i local_inventory -e "@group_vars/rdomain.yml" -e 'rdomain=true' vagrant-pb.yml
````
