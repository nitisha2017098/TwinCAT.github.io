<h1> History of PLC </h1>
. Before PLC’s Relay Logic was used for industrial automation which had several drawbacks, major one was that an damage to a single wire cause interruption to whole automation process.

. To solve this, PLC (Programmable logic controllers) were introduced.

. Very first PLC was invented in 1969, but it was very slow.

. In 1979 PLC’s new generation was introduced which was very fast and reliable than the old one.

<h1>About Twincat</h1>

. TwinCAT stands for “ The Windows Control and Automation Texhnology.

. It is a visual studio based software.

. TwinCAT has two parts
	-  XAE: eXtanded Automtion Engineering
	- XAR: eXtanded Automation Runtime

. And three states: Config, Run, Stop/exception 

. TwinCAT allows us to use any machine (for example this PC) as a PLC.

<h1>Advantage of using TwinCAT</h1>
. CPU process the various processes depending upon the priorities of the task. For industrial automation process should be fast so TwinCAT uses isolated cores of CPU  for compling and to run code so here is a plus point for TwinCAT over other softwares.

<h1> HELLO WORLD Program</h1>
1. Open TwinCAT application and click new project and name the project as Helloworld.

2. Click “ok”.

3. Use ADSLOGSTR fuction to display message.

4. ADSLOGSTR consist message type, format string and string argument.
![image](https://user-images.githubusercontent.com/59726765/216982599-50e54281-d20b-4c22-aa8c-ba8a01d52c91.png)

<h1> Data Types in TwinCAT</h1>
A data type, in programming, is a classification that specifies which type of value a variable has and what type of mathematical, relational or logical operations can be applied to it without causing an error. A string, for example, is a data type that is used to classify text and an integer is a data type used to classify whole numbers.
![image](https://user-images.githubusercontent.com/59726765/216982883-ddae84f8-cd4f-4259-8ac4-96e1239114a7.png)
![image](https://user-images.githubusercontent.com/59726765/216982953-b55397d3-5a6a-497b-b073-944508a1a877.png)
![image](https://user-images.githubusercontent.com/59726765/216983067-9c073901-b664-4ec4-99cc-9abfc0b03ae8.png)

<h1>Enum</h1>
Enumeration (or enum) is a user defined data type. It is mainly used to assign names to integral constants, the names make a program easy to read and maintain.
![image](https://user-images.githubusercontent.com/59726765/216983303-1029c362-0724-4316-8b26-50e0cef91c23.png)

<h1>Adding Enum in TwimCAT: </h1>
![image](https://user-images.githubusercontent.com/59726765/216983459-383912bc-74b6-40d1-94b3-3ec85d28aad7.png)


<h1>Array</h1>
Array is set if integers

Arrays in TwinCAT:

<h1>Two methods to declare arrays in TwinCAT</h1>
![image](https://user-images.githubusercontent.com/59726765/216985033-2a01a6c8-8907-41d9-b27a-d4d464a2dd37.png)

![image](https://user-images.githubusercontent.com/59726765/216984668-f0170cfe-a0e1-46b0-9e5e-a3a6e9a5c172.png)

<h1>Instructions</h1>
<h5>IF</h5>
If is used to specify a block of code to be excecuted if a specified condition is true.

```python
IF condition Then
	// Block of code to be executed
END_IF
```
   
   


