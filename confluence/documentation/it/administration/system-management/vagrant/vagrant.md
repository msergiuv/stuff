[[home]](../../../../home.html) 
[[system-operations]]()

> **Vagrant**

[oficial site](https://www.vagrantup.com/)   
[oficial documentation](https://docs.vagrantup.com/v2/) 

- [Definition](#definition)
- [Tutorials](#tutorials)
- [Steps to install](#steps)
- [Vagrant project setup](#setup)


<a name="definition"></a>
> **Definition:** [(more)](https://www.virtualbox.org/wiki/Virtualization)

***Vagrant*** is a command line script for ***VirtualBox, VMware, AWS***. It will isolate dependencies and their configuration within a single disposable, consistent environment, without sacrificing any of the tools you're used to working with (editors, browsers, debuggers, etc.). Once you or someone else creates a single ***Vagrantfile***, you just need to ***vagrant up*** and everything is installed and configured for you to work. [(more)](https://docs.vagrantup.com/v2/why-vagrant/index.html) 

**Baseboxes** are virtual machine images. This is the default start state of your VM. Think of setting up a new VM, then saving a snapshot so that you can restore to that point any time you want.

There are created baseboxes [already](http://www.vagrantbox.es/), so you don't need to create your own. The default is lucid32, an ubuntu basebox.
    

<a name="tutorials"></a>
> **Tutorials:** <br/>

- [vagrant with chef](http://adamcod.es/2013/01/15/vagrant-is-easy-chef-is-hard.html#fn1) 
- [introduction to vagrant](https://www.youtube.com/watch?v=FSxS6iPJMFw)
- [vagrant beginner](https://www.youtube.com/watch?v=ZGUEjZckijA)

  
<a name="steps"></a>
> **Steps to install:**

 - download [vagrant](https://www.vagrantup.com/downloads.html)
 - follow [steps](https://docs.vagrantup.com/v2/installation/index.html)

<a name="setup"></a>
> **Project setup:**

- initialization [(more)](https://docs.vagrantup.com/v2/getting-started/project_setup.html)

		# initializing a vagrant project directory
		# after init will place a Vagrantfile in the project directory
	    $ vagrant init

	The VagrantFile is filled with comments and examples

- boxes [(more)](https://docs.vagrantup.com/v2/getting-started/boxes.html)

		# downloads new box locally
		# title that reference the box to be used in the vagrant projects
		# url - download box location
		$ vagrant box add <title> <url>

	Boxes can be added from [vagrant cloud](https://vagrantcloud.com/boxes),  [already created](http://www.vagrantbox.es/), file, custom url, etc.
	The box is installed locally, the the vagrant project uses it as initial image to clone from, and never modifies the actual base image.

- to be used a box as a base in the project have to be configured as follows: 

		# add in Vagrantfile
   		Vagrant.configure("2") do |config|
  			config.vm.box = "title to reference locally downloaded box"
		end

	If the box wasn't added before, Vagrant will automatically download and add the box when it is run.

		# boot/starts vagrant environment if it's not running already
		$ vagrant up

		# interaction with virtual machine
        # vagrant uses its own private/public keys which are automatically 
		# copied to the VM, so there's no username/password to worry about.
		$ vagrant ssh

		# remove all traces of the virtual machine
		$ vagrant destroy

 		# saves the machine state and temporarily shuts down the VM
		# running vagrant up will bring it back again exactly as it was
		$ vagrant suspend

		# re-runs provisioner of choice (e.g. if you've updated something) without having to start from scratch)
		$ vagrant provision

		# resets the VM to the basebox's original state and re-runs provisioner.	
		$ vagrant reload

		# completely removes all trace of the VM from the system 
		# (except the basebox or provisioner)
		$ vagrant destroy


- synced folder (by default, vagrant will share your project directory, the directory with the Vagrantfile to /vagrant) [(more)](https://docs.vagrantup.com/v2/synced-folders/basic_usage.html)

		config.vm.synced_folder "src/", "/srv/website"

