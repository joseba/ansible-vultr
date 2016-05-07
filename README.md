# ansible-vultr
Ansible module for managing servers on [Vultr](http://www.vultr.com/?ref=6823697).
At the moment the module supports __only__ server __creation and destruction__.

## Installation
* Install [Ansible 2.0](http://docs.ansible.com/ansible/intro_installation.html)

* Copy master.ini.dist to ~/master.ini and change the variables to your needs.

* Clone the repo and enjoy!
```sh
$ git clone git@github.com:joseba/ansible-vultr.git
```

## Usage: create project
Launch and provision a new project on VULTR.
```sh
$ ansible-playbook create_testproject.yml
```
What this Playbook do for you?
- Deploy servers
- Prepare hosts file  
- Prepare ansible inventory file
- Configure private network

## Usage: destroy project
TODO

## Known issues
When you deploy a __new__ server on Vultr, you should wait until initialization finishes.
In ansible we accomplish this using __wait_for__ module. Below, the first task that should run on all servers is **to wait for port 22** to become available.
Once port 22 is active - ping all servers. At this step port 22 may have become available, but your ssh key has not been copied to authorized_keys yet. Hence you will get __denied access error__. Rerun the playbook 2-3 seconds later, all should go fine.
