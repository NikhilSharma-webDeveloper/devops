# How to use Vagrant

## Basic SetUp [(link)](https://developer.hashicorp.com/vagrant/tutorials/getting-started/getting-started-index)

`TIPS:- Vagrant file is most important in Vagrant as it will help to set the entire vm characteristics` [(TEMPLATE)](https://developer.hashicorp.com/vagrant/tutorials/getting-started/getting-started-project-setup)
    

### 1. Initilizing
    vagrant init "name of the vagrant image or file"

    ## This will create vagrant file in the directory

### 2. To turn on vagrant vm
    vagrant up "you can add name of vms too if you want"

### 3. To destroy vagrant vm
    vagrant destroy "name of vms"

### 4. Set Up directory
    The directory in which you initilize your vagrant will act as an base directory for vm

### 5. To ShutDown VM
    vagrant halt

     # This will gracefully stop the vm 

### 6. To View all the vargant boxes in machine 
    vagrant box list
    
    # to list all the downloaded boxes in your machine by vagrant 

### 7. To View the status of VMS 
    vagrant status

    # it will list all the boxes with their current status

### 8. Connect to Vm from local machine
    vagrant ssh

    To connect to vm use the command

### 9. To Reboot VM use Command 
    vagrant reload

    It will view all the changes in the vagrant files

### 10. Status of all global VMS
    vagrant global-status

    To view the status of all the globally available vms in machine

