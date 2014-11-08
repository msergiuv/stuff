[[home]](../../../../home.html) 

> **Chef**

[(oficial site)](https://www.getchef.com/)
[(Oficial chef documentaion)](http://learn.getchef.com/) 
 

- [Definition](#definition)
- [Tutorials](#tutorials)
- [Installation](#installation)
- [Tests](#tests)


<a name="definition"></a>
> **Definition:** <br/>
Chef is a systems and cloud infrastructure automation framework that makes it easy to deploy servers and applications to any physical, virtual, or cloud location, no matter the size of the infrastructure. Each organization is comprised of one (or more) workstations, a single server, and every node that will be configured and maintained by the chef-client. Cookbooks (and recipes) are used to tell the chef-client how each node in your organization should be configured. The chef-client (which is installed on every node) does the actual configuration.
    

<a name="tutorials"></a>
> **Tutorials:** <br/>


  
<a name="installation"></a>
> **Installation:** 

 **Chef has 3 main parts:**<br/>
 
- [Chef server](#chef-server)
- [Chef client (nodes)](#chef-client)
- [Chef administrator's workstation](#chef-admin)

<a name="chef-server"></a>
> **Chef Server installation steps**

- m_sergiuv (default+c)

> **Chef Client (node) setup steps**
<a name="chef-client"></a>

*Install the Chef client on every node to manage with Chef. The Chef client and the Chef server works together to bring nodes to their desired states using policies you provide as recipes.*

Example for node that runs on ***ubuntu***:

1. To install the chef client on a node run the following command in the shell (or install manually the package):

		curl -L https://www.opscode.com/chef/install.sh | sudo bash
		# 1. follows the redirection and downloads the install.sh
		# 2. starts a bash shell as a root level user, because normal user can't access /home/  


<a name="chef-admin"></a>
> **Chef Administration workstation setup steps**

- Commands: 

    	$ knife --version
		# shows the version of chef client installed on admin workstation
		$ knife client list 
		# can be executed in the chef-repo directory
		# list list of clients ([name of the organisation]-validator) 




<a name="tests"></a>
> **Tests:**<br/>
> Test data:<br/>
	External Address:	uvo14kvzinnc7el26bk.vm.cld.sr <br/>
	Internal IP:	    10.160.201.90 <br/>
	Username:	root <br/>
	Password:	Ee03EYIcW6 <br/>