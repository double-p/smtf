This is my project "pf+rdomains create splendid multi-tenant firewalls".
For reading please use the 'latest' version "asiabsdcon2017-talk.pdf" and
"asiabsdcon2017-paper.pdf".

Workflow for the virtualized testing environment:
- install 'vagrant', 'packer' and 'ansible' (homebrew available)
- create a baseimage and import -> ./Packer/README.md
- run the two playbooks  -> ./ANSIBLE.md
- may check the provisioned hostname.if and 'sh /etc/netstart'
  in each VM or reboot: 'vagrant reload'
- Fun+Profit!

