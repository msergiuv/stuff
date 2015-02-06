[[home]](../../../../home.html) 

> **Tutorial**

[oficial site]()<br/>
[oficial documentation]()
 

- [What is a variable](#var_def)
- [Variable type](#type_def)


<a name="var_def"></a>
> **Variable definition:**

Variable is a storage location paired with an associated symbolic name which contains some known or unknown quantity or information referred to as a value. The variable name is the usual way to reference the stored value.
The identifier in computer source code can be bound to a value during run time, and the value of the variable may thus change during the course of program execution. A variable has data type, the type of value that the variable  can hold. 
Once variable declared it must be initialized with a value, that means that once variable has been created in a memory must have a value when the variable is used.


<a name="type_def"></a>
> **Variable type:**


<table>
	<th>Type</th>
	<th>bit (allocated space in memory)</th>
	<th>byte</th>
	<th>min value</th>
	<th>max value</th>
	<th>default value</th>

	<tr>
		<td>byte</td>
		<td>8</td>	
		<td>1</td>	
		<td>-128</td>
		<td>127</td>
		<td>0</td>
	</tr>

	<tr>	
		<td>short</td>
		<td>16</td>	
		<td>2</td>	
		<td>-32768</td>
		<td>32767</td>
		<td>0</td>
	</tr>

	<tr>
		<td>int</td>
		<td>32</td>	
		<td>4</td>	
		<td>-2147483648</td>
		<td>2147483647</td>
		<td>0</td>
	</tr>

	<tr>
		<td>long</td>
		<td>64</td>	
		<td>8</td>	
		<td>-922372036854775808</td>
		<td>922372036854775807</td>
		<td>0L</td>
	</tr>
	
	<tr>
		<td>char</td>
		<td>16</td>	
		<td>2</td>	
		<td>0</td>
		<td>65536</td>
		<td>\u0000</td>
	</tr>

</table>


<table>
	<th>Type</th>
	<th>bit (allocated space in memory)</th>
	<th>byte</th>
	<th>Range</th>
	<th>default value</th>
	<th>Precision</th>
	
	<tr>
		<td>float</td>
		<td>32</td>	
		<td>4</td>	
		<td>3,4e-38 < |x| < 3,4e38</td>
		<td>0.0f</td>
		<td>7-8 digits</td>
	</tr>

	<tr>
		<td>double</td>
		<td>64</td>	
		<td>4</td>	
		<td>1.7e-308 < |x| < 1.7e308</td>
		<td>0.0d</td>
		<td>17 digits</td>
	</tr>
</table>