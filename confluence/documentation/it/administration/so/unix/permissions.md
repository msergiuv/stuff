[[home]](../../../../home.html) 
[[system-operations]]()

> **Unix permissions**

[oficial site](https://www.getchef.com/)
 

- [Definition](#definition)
- [Modes](#modes)


<a name="definition"></a>
> **Definition:** <br/>
what is a permission?

<a name="modes"></a>
> **Modes:** <br/>

***There are 3x3 bit flags for a mode:<br/>***

 - (owning) User
	- read
	- write
	- execute
 - Group
	- read
	- write
	- execute
 - Other
	- read
	- write
	- execute

***So each triple encodes nicely as an octal digit.<br/>***
<table>
	<th>rwx</th>
	<th>oct</th>
	<th>meaning</th>
	<tr>
		<td>001</td>
		<td>1</td>
		<td>execute</td>
	</tr>
	<tr>
		<td>010</td>
		<td>2</td>
		<td>write</td>
	</tr>
	<tr>
		<td>011</td>
		<td>3</td>
		<td>write & execute</td>
	</tr>
	<tr>
		<td>100</td>
		<td>4</td>
		<td>read</td>
	</tr>
	<tr>
		<td>101</td>
		<td>5</td>
		<td>read & execute</td>
	</tr>
	<tr>
		<td>110</td>
		<td>6</td>
		<td>read & write</td>
	</tr>
	<tr>
		<td>111</td>
		<td>7</td>
		<td>read & write & execute</td>
	</tr>
</table>
    

**For example:** 0644 is:

* (owning) User: read & write
* Group: read
* Other: read
<br/>*This might also be written:*<br/>
-rw-r--r--

Whereas full permissions, 0777 can also be written:<br/>
-rwxrwxrwx

*So the octal number passed to create corresponds directly (via bit-pattern) to the file permissions as displayed by ls -l.*
[[Details]](http://ss64.com/bash/chmod.html)