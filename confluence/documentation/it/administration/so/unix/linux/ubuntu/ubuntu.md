[[home]](../../../../home.html) 
[[system-operations]]()
> **Ubuntu**  
[oficial site](http://www.ubuntu.com/)<br/>

 

- [Definition](#definition)
- [Commands description](#commands)
- [Unix directories](#directories)
- [root account](#root_account)

- [Tutorials](#tutorials)
- [Details](#details)


<a name="definition"></a>
> **Definition:** <br/>

<a name="directories"></a>
> **Unix directories:** [(more)](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

- [opt](#opt)

<a name="opt"></a>
> **opt directory:** [(more)](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html)

**/opt** - the directory is reserved for all the software and add-on packages that are not part of the default installation


<a name="commands"></a>
> **Commands description:**

- [pwd](#cmd_pwd)
- [clear](#cmd_clear)
- [curl](#cmd_curl)
- [shutdown](#cmd_shutdown)
- [ipconfig](#cmd_ipconfig)
- [grep](#cmd_grep)
- [dpkg](#cmd_dpkg)


<a name="cmd_pwd"></a>
> **pwd command:** [(more)](http://manpages.ubuntu.com/manpages/precise/man1/pwd.1posix.html)

pwd - return working directory name

Options: pwd [-L, -P]. If  both -L and -P are specified, the last one shall apply.  If neither -L nor -P is specified, the pwd utility shall behave as if -L had  been specified.

<a name="cmd_clear"></a>
> **clear command:** <br/>

	clear - shifts previous output upwards
	reset - completely re-initialise the terminal

<a name="cmd_curl"></a>
> **curl command:** [(more)](http://www.thegeekstuff.com/2012/04/curl-examples/) <br/>

**curl** is a software package which consists of command line tool and a library for transferring data using URL syntax.

**curl**  supports various protocols: 
[DICT, FILE, FTP, FTPS, Gopher, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMTP, SMTPS, Telnet and TFTP]

Examples:

    $ curl http://www.centos.org	
	#gets the content and displays in the STOUT
	
	# can be used: [>, -o, -O] options to move the result to a file 
	$ curl http://www.centos.org > centos-org.html	
	#stores the content in a file and shows download statistics
	$ curl -o mygettext.html http://www.gnu.org/software/gettext/manual/gettext.html
	# -o the content is saved in the file provided in the cmd line
	$ curl -O http://www.gnu.org/software/gettext/manual/gettext.html
	# -O the content is saved in the file named gettext.html
	$ curl -O URL1 -O URL2
	# downloads multiple files in a single shot

	$ curl -C - -O http://www.gnu.org/software/gettext/manual/gettext.html
	# -C continue/resume the download from where it off earlier

	$ curl --limit-rate 1000B -O http://www.gnu.org/software/gettext/manual/gettext.html
	# limit the rate of data transfer. The above option limits to 1000 Bytes/second

	$ curl -z 21-Dec-11 http://www.example.com/yy.html
	# -z downloads a file only if it was modified before the given time.
	# works for HTTP and FTP

	$ curl -u username:password URL
	# -u for contents that requeres auth to be viewed.
	# curl uses Basic HTTP auth by default. 
	# To specify other methods of auth ca be used -ntlm | -digest

	$ curl -u ftpuser:ftppass -O ftp://ftp_server/public_html/xss.php
	# download files from ftp server 

	$ curl -u ftpuser:ftppass -O ftp://ftp_server/public_html/
	# URL refers to a directory. Will list all files/directories under URL

	$ curl ftp://ftp.uk.debian.org/debian/pool/main/[a-z]/
	# files given in  a range will be downloaded

	$ curl -u ftpuser:ftppass -T myfile.txt ftp://ftp.testserver.com
	# uploads file to FTP server

	$ curl -u ftpuser:ftppass -T "{file1,file2}" ftp://ftp.testserver.com	
	# uploads range of files to FTP server 

	$ curl -v http://google.co.in
	# -v option enables the verbose mode and it will print the details
	# -trace for more detailed information

	$ curl dict://dict.org/d:bash
	# gets the definition for a word with the help of DICT protocol
	$ curl dict://dict.org/show:db
	# list all dictionaries
	$ curl dict://dict.org/d:bash:foldoc
	# foldoc dictionary finds definitions in computer meaning

	$ curl -x proxysever.test.com:3128 http://google.co.in
	# -x uses a proxy to download a file

	$ curl --mail-from blah@test.com --mail-rcpt foo@test.com smtp://mailserver.com
	# send mail using SMTP protocol

	 

<a name="cmd_shutdown"></a>
> **Command to shutdown or reboot computer:** [(more)](http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/) 

- shutdown (shutdown arranges for the system to be brought down in a safe way. All logged-in users are notified that the system is going down and, within the last five minutes new logins are prevented)

For additional options [*command* --help] 

	$ sudo shutdown -h now
	$ sudo shutdown -h 0
    $ sudo poweroff
	$ sudo halt				#intended to instruct the kernel to reboot or halt
	$ sudo init 0
	$  sudo shutdown -h 18:45 "The computer will be shutdown at specified time"

- restart

	    $ sudo reboot
		$ sudo shutdown -r now
		$ sudo init 6

<a name="tutorials"></a>
> **Tutorials:**

- [How to install ubuntu, step by step](http://ubuntuserverguide.com/2014/04/how-to-install-ubuntu-server-14-04-trusty-tahr.html)

<a name="cmd_ipconfig"></a>
> **ipconfig command:**<br/>
> network info

	#displays interfaces with assigned ip
	$ ifconfig 		
	#displays all interfaces whether or not has assigned an ip
	$ ifconfig -a		
	
	$ ip addr show
	
	#assigning IP to interface
	$ ifconfig eth0 192.168.1.200/24 up 	
	#default route	
	$ route add default gw 192.168.1.1 		
		
	# displays public IP
	$ curl ipecho.net/plain ; echo			
	$ curl ifconfig.me

<a name="cmd_grep"></a>
> **grep command:** [(more)](http://www.tecmint.com/12-practical-examples-of-linux-grep-command/)

*The grep command is used to search text or searches the given file for lines containing a match to the given strings or words. By default, grep displays the matching lines. Use grep to search for lines of text that match one or many regular expressions, and outputs only the matching lines.*
 
	grep 'word' filename
	grep 'word' file1 file2 file3
	grep 'string1 string2'  filename
	grep --color 'data' fileName

	$ dpkg –l | grep –i chef		
	# searches through installed packages everything with "chef" in it
	# dpkg –l lists installed *.deb packages on system, and piped output to grep
	# grep -i string filters out, option -i ingores case

	$ grep –v “string”  /etc/apache2/file
	# -v option inverts the output and prints non matching lines   
 
  	$ find . –name “*.mp3” | grep –i JayZ | grep –vi “remix”
	# finds all files with .m3 extension
	# piping to grep -i filters out and prints files with the name 'JayZ'
	# piping to grep -vi filter out does not print files with string “remix”. 

<a name="cmd_dpkg"></a>
> **dpkg command:** [(more)](http://www.howtogeek.com/howto/ubuntu/see-where-a-package-is-installed-on-ubuntu/)

Where a package was installed

    dpkg -L <packagename>


<a name="root_account"></a>
> **Enabling the root account:** [(more)](https://help.ubuntu.com/community/RootSudo)

    $ sudo -i		
	# run login shell as the target user
	
	$ sudo passwd root
	# enables root account and sets a password

	$ sudo passwd -dl root
	# Re-disabling root account

<a name="details"></a>
> **Details:**

