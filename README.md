# ansible-setup
Ansible installation and setup

Agenda:- Installing asible on master node and we will try to orchestrate two slave node using master server.

Pre-requisite:- We required 3 ubuntu server with 2 vcpu and 4 gb ram and ssh port 22 should be open.

Steps:-
step 1) :- login into master server and run belw command to install ansibel.
````
>	sudo su -
>	sudo apt update 
>	sudo apt install software-properties-common
>	sudo apt-add-repository --yes --update ppa:ansible/ansible
>	sudo apt install ansible
>	ansible --version
````
step 2) genrate ssh key using below command on all three servers.
````
>	ssh-keygen -t rsa -b 4096
````

step 3) Open .ssh folder and copy id_rsa.pub key into autharize_key file.

sttep 4) create a folder rgerading your application.
````
>	mkdir app_name
````
step 5) Create inventory file in master node.
````
>	cd app_name
>	vi hosts
[app-servers]
app-server1 ansible_host=host_ip ansible_user=root
app-server2 ansible_host=host-ip ansible_user=root

>	ansible all --list-hosts
````
step 6) create ansible play-book in master server.
````
---
- hosts: all
  tasks:
    - name: Print message
      debug:
        msg: Hello Ansible World
  tasks:
    - name: Create a file
      file: path=/home/server.conf state=touch
 ````
step 7) run below command to confirm connectivity between all servers.
````
>	ansible all -i hosts -m ping
````
step 8) run below command to deploy playbook.
````
>	ansible-playbook -i hosts playbook.yaml
````

###########Thank you###############
Please like and share this video
This installation document is available at below git link
https://github.com/LOKI0307/ansible-setup


