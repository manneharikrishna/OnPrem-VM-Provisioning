Role Name: 
vmware_vm


Playbook name: 

vmware_vm_build.yml

	#- hosts: all
	- hosts: localhost
	  gather_facts: no
	  connection: local
	  become: True

	  roles:
              - role: vmware_vm




To run the vmware build code.


This role is designed to build Virtual machines in vmware. It has been tested against vcenter 7.

Some important default variables are:


create_vm: Yes (When you want to create a VM. You must set this value to "No" if you want to destroy ALL VMs.)

destroy_vm: No (Set this value to "Yes" if you want to destroy ALL VMs.)

vm_count: 0 (Set this value to the number of VMs you want to build. For example vm_count: 10 will build 10 VMs in Vmware)

windows_machine: 0 (You must set this to "True" if the machine you are building is a windows server)
                   This applies to windows server 2019, windows server 2016, windows server 2012.


centos_7_server: 0  (You must set this to "True" if the server you want to build is centos 7)

win_server_2019: 0 (You must set this to "True" if the machine you are building is Windows server 2019)

win_server_2016: 0 (You must set this to "True" if the machine you are building is Windows server 2016)

win_server_2012: 0 (You must set this to "True" if the machine you are building is Windows server 2012)



EXAMPLES

##### TO BUILD A SINGLE CENTOS 7 VM  #########################
ansible-playbook vmware_vm_build.yml --connection=local -e "vm_count=1 centos_7_server=True"


######## TO BUILD A SINGLE WINDOWS SERVER 2019 VM ###################
ansible-playbook vmware_vm_build.yml --connection=local -e "vm_count=1 win_server_2019=1 windows_machine=1"

########### TO DESTROY ALL VMs ##########
ansible-playbook vmware_vm_build.yml --connection=local -e "destroy_vm=1 create_vm=0 vm_count=1 centos_7_server=1"

######## TO BUILD A SINGLE WINDOWS SERVER 2016 VM ###################
ansible-playbook vmware_vm_build.yml --connection=local -e "vm_count=1 win_server_2016=1 windows_machine=1"

######## TO BUILD 10 WINDOWS SERVER 2016 VMs ###################
ansible-playbook vmware_vm_build.yml --connection=local -e "vm_count=10 win_server_2016=1 windows_machine=1"


######## TO BUILD A SINGLE WINDOWS SERVER 2012 VM ###################
ansible-playbook vmware_vm_build.yml --connection=local -e "vm_count=1 win_server_2012=1 windows_machine=1"



