[[home]](../../../../home.html) 

> **Spring data**

[oficial site](https://www.playframework.com/)<br/>
[oficial documentation](https://www.playframework.com/documentation/2.3.x/Home)
 

- [Definition](#definition)
- [Tutorials](#tutorials)
- [Details](#details)
- [Installing Play](#play_install)


<a name="definition"></a>
> **Definition:** <br/>

<a name="tutorials"></a>
> **Tutorials:** <br/>

  
<a name="details"></a>
> **Details:**<br/>

- LIKE using input parameter

		# match start
		LIKE CONCAT('%',:param)
		# match end
		LIKE CONCAT(:param,'%')
		# constains
		LIKE CONCAT('%', :param,'%')
		
	
	
