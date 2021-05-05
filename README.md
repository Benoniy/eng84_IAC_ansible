# Infrastructure as code
## Types:
* mutable/immutable
* cloud/local


## What is it?  
* The provisioning and management of servers/software through YAML files  
* fast and simple  
* constant  
* low risk  


## Best practises  
* codify everything  
* Low documentation  
* Version Control  
* CI/CD  
* Security  


## Two parts of IAC (infrastructure as code):
### Configuration management  
* Responsible for provisioning and maintaining systems:  
    * Chef  
    * Ansible  
    * Puppet  
    
### Orchestration
* Uses script's to talk to the cloud and deploy the templates defined by configuration management.
    * CloudFormation (AWS)  
    * Ansible  
    * Terraform
    

# Ansible
* Uses SSH to control agent nodes  
* If you write a script for one platform (aws) then you can easily switch to another (azure)  
* No previous knowledge needed
* Use ad-hock commands for simple operations (run a command on an agent and get the return)

### Diagram:  

![alt Text]("images/ansible.png")

### AdHoc commands:  
* `ansible host -a "command"` - Run a command on a host and get the result  
* `ansible host -m "command"` - run a command related to the host using a module
  * `-m` - Specifies a module
  * `-a` - Means adhoc
  

### Example of adhoc commands:  
* `ansible all -a "uptime"`
* `ansible all -a "sudo apt-get update -y"`
* `ansible all -a "sudo apt-get upgrade -y"`


### How do I make a YAML playbook file?  
* `/etc/ansible/playbook_name.yml`
```
# YAML files start with 3 hyphens (---)
---

# define the agents we will work on
- hosts: web

#
  gather_facts: yes

# administrator privileges?
  become: true

# Sequential set of commands to be ran on the agents
# All tasks are named for output purposes
  tasks:

  # Name of the task
  - name: Installing nginx
    # Operations of the task
    apt: pkg=nginx state=present
    notify:
    - name: Enable nginx at boot
      service: name=nginx state=restarted enabled=yes
```
