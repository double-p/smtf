packer
------
- adapt ./OpenBSD-config.json if need be.
- download install60.iso and adapt ./OpenBSD-60.json for 'iso_url'.
````
$ packer build -var-file=OpenBSD-config.json OpenBSD-60.json
````

vagrant
-----
````
$ vagrant box add obsd60 packer_vbox-obsd60-amd64_virtualbox.box
````
The name 'obsd60' has to match 'openbsd_vbox' in 'group_vars/all.yml'.
