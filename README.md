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


### AdHoc commands:  
* `ansible host -a "command"` - Run a command on a host and get the result  
* `ansible host -m "command"` - run a command related to the host using a module
  * `-m` - Specifies a module
  * `-a` - Means adhoc
  

### Example:  
* `ansible all -a "uptime"`
* `ansible all -a "sudo apt-get update -y"`
* `ansible all -a "sudo apt-get upgrade -y"`