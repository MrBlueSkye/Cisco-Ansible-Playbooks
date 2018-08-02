# Cisco-Ansible-Playbooks

Ansible is a powerful tool that has become very popular in application deployment, service provisioning and general IT automation tasks. Ansible uses a system of "playbooks" written in YAML to describe automation and configuration management jobs.

#### This is the process Ansible usually uses when executing a task on a managed node (see Introduction to Ansible video from Ansible for Networking Engineers webinar for more details).

-Collect the Python code that is required by the task (module source code + libraries referenced by the module);
-Open an SSH connection to the managed node;
-Copy source code to a temporary directory on the managed node;
-Execute Python code on the managed node;
-Collect results and return them to Ansible playbook.


#### Most of these steps cannot be executed on a typical switch or router. Networking modules thus use a different approach:

-Python code is executed on Ansible host;
-The code executed on Ansible host generates commands to be sent to the managed device, open SSH or NETCONF connection to the managed device, and executes the commands;
-The printouts generated by the managed device are parsed and returned as module results to Ansible playbook.

### Official Docs
https://docs.ansible.com/ansible/2.4/ios_command_module.html
https://docs.ansible.com/ansible/2.5/network/getting_started/first_playbook.html#run-your-first-command-and-playbook

### Main Ansible configuration file 
/etc/ansible/ansible.cfg

### Run Playbook against specified hosts
sudo ansible-playbook -i host-file playbook-file.yml

### CLI Flags
-i      //specify inventory file
-k      //provide SSH password at prompt

### Commands
ansible all -m ping     //ping every host in group [all]
ansible routers -m ping     //ping every host in group [routers]
