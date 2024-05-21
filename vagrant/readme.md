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

### 11. All VM Information
    There is an directory located at ~/vagrant.d which will have all the information about all the boxes we have downloaded as well as alot of more details about all boxes

## Understanding Vagrant File

- Vagrant use Ruby script for config
- Config start from 
    `Vagrant.configure("2") do |config|` 
    and ends at `end`
- `("2")` it is the version of vagrant
- config between `|config|` act as an variable so when ever we are modifying and configuration we are using it like `config.vm.box = "ubuntu/jammy64"`
- `config.vm.network "public_network"` This will just enable the bridge adapter on your vm. There are more setting available please see documentation
- There is another both called `config.vm.provider "virtualbox" do |vb|`. In this block we allocate ram, gpu and other resourses and it also end with `end`
- We can make shareed folder with `config.vm.synced_folder "../data", "/vagrant_data"` second argument is parent os path and third is child os directory [Link](#vagrant-sync-directories)
- Provisioning happens in these lines 
`config.vm.provision "shell", inline: <<-SHELL
    " Code you want to use to automate"
  SHELL`
  [Link](#vagrant-provisioning)

## Vagrant Sync Directories
Synced folders enable Vagrant to sync a folder on the host machine to the guest machine, allowing you to continue working on your project's files on your host machine, but use the resources in the guest machine to compile or run your project.

- If you are using the Vagrant VirtualBox provider, then VirtualBox shared folders are the default synced folder type. These synced folders use the VirtualBox shared folder system to sync file changes from the guest to the host and vice versa.
- So if we make any file in the folder where vagrant is running the changes will be reflected in both guest and host OS. 
- In Vm it is in ~/vagrant.
- We can make shareed folder with `config.vm.synced_folder "../data", "/vagrant_data"` second argument is parent os path and third is child os directory
- In windows while giving path rather than using `/` use `\\`
- There are alot more we can do for that follow docs

## Vagrant Provisioning

Provisioners in Vagrant allow you to automatically install software, alter configurations, and more on the machine as part of the vagrant up process.

Provisioning happens at certain points during the lifetime of your Vagrant environment:

- On the first `vagrant up` that creates the environment, provisioning is run. If the environment was already created and the up is just resuming a machine or booting it up, they will not run unless the --provision flag is explicitly provided.

- When `vagrant provision` is used on a running environment.

- When `vagrant reload --provision` is called. The --provision flag must be present to force provisioning.

Provisioning happens in these lines 
`config.vm.provision "shell", inline: <<-SHELL
    " Code you want to use to automate"
  SHELL`