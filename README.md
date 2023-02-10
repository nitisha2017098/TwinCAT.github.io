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

<h1>TwinCAT program to Start and Stop motor axis Using ST</h1>

MAIN (PRG):
```python
PROGRAM MAIN
VAR
	ExampleAxisName : AXIS_REF;
	ExAxPower 		: MC_Power;
	ExAxStop 		: MC_Stop;
	ExAxMvVelo 		: MC_MoveVelocity;
	
	State			: INT := 0;
	
	start			: BOOL;
	stop			: BOOL;
	
END_VAR
```
MAIN WIMDOW:
```python
ExampleAxisName.ReadStatus();

CASE State OF
	0:	//power activation
		ExAxPower.Enable := TRUE; 
		ExAxPower.Enable_Positive := TRUE;
		ExAxPower.Enable_Negative := TRUE;
		State := 1;
		
	1:	//check power
		IF ExAxPower.Active THEN
			State := 2;
		END_IF
		
	2:	//start motion
		IF start THEN
			
			ExAxMvVelo.Velocity := 50; //arbitrary number
			ExAxMvVelo.Execute := TRUE;
			State := 3;
		END_IF
		
	3:	//check that motion is within range
		IF ExAxMvVelo.InVelocity THEN
			State := 4;
		END_IF
		
	4: //stop motion
		IF stop THEN
			ExAxStop.Execute := TRUE;
			start:= False;
			State := 5;
		END_IF

		
	5: //check for stop to finish
		IF ExAxStop.Done THEN
			stop := FALSE;
			State := 2;
		END_IF
		
END_CASE

ExAxPower(Axis := ExampleAxisName);
ExAxStop(Axis := ExampleAxisName);
ExAxMvVelo(Axis := ExampleAxisName);
```

Steps:

1. The first step to use any of the motion control tools in a PLC program is to import the Tc2_MC2 library.To import the Tc2_MC2 library, go into the Solution Explorer and scroll down to the PLC section. Expand the PLC section and look for the References tab. Right click the References tab and select Add library..., then type "MC2" into the search box. Find the Tc2_MC2 library, select it and hit OK.

![Screenshot (226)](https://user-images.githubusercontent.com/59726765/218043064-0386cabb-f731-4265-9573-2408546a3e4f.png)
![Screenshot (227)](https://user-images.githubusercontent.com/59726765/218043273-2df587d9-8203-4378-9bd0-cb6de326d247.png)

2. use ExAxName as the name of our function block. To declare our instance, we type ```ExAxName : AXIS_REF;``` into the Variable Declaration Window. AXIS_REF function block allows us to link our hardware to the PLC program. It also gives us access to the ReadStatus() function. Calling ReadStatus() will update the local I/O variables that are linked to our axis.

Variable Declaration Window:
```
PROGRAM MAIN
VAR
	ExAxName : AXIS_REF;
END_VAR
```
Code Window:
```
ExAxName.ReadStatus();
```

3. MC_Power function block allows us to control the software enable for our axis. If we don't enable MC_Power, any command we send to our axis will result in an error. Let's add an instance of MC_Power to our POU. We'll call our new function block ExAxPower. To declare our instance of MC_Power, we need to type ExAxPower : MC_Power into the Variable Declaration Window.

```
PROGRAM MAIN
VAR
	ExampleAxisName : AXIS_REF;
	ExAxPower 		: MC_Power;
END_VAR
```

4. MC_Stop function block enables us to stop the axis. Call a function ``ExAxStop : MC_Stop``` in variable declaration window.

```
PROGRAM MAIN
VAR
	ExampleAxisName : AXIS_REF;
	ExAxPower 		: MC_Power;
	ExAxStop 		: MC_Stop;
	
END_VAR
``` 
5. MC_MoveVelocity function block enables us to control the velocity of rotation. Call a function ```ExAxMvVelo : MC_MoveVelocity; in variable declaration window.

	```
	PROGRAM MAIN
	VAR
		ExampleAxisName : AXIS_REF;
		ExAxPower 		: MC_Power;
		ExAxStop 		: MC_Stop;
		ExAxMvVelo 		: MC_MoveVelocity
	END_VAR
	``` 

6. CASE Function is used to axcecute the code blocks at different states i.e. for starting, running and stoping. CASE function compares the variable passed into it, and executes the section of code where it finds a match.
8.. Integer variable "State" is declared in variable declaration window for case function which contains value "0".

```
PROGRAM MAIN
VAR
	ExampleAxisName : AXIS_REF;
	ExAxPower 		: MC_Power;
	ExAxStop 		: MC_Stop;
	ExAxMvVelo 		: MC_MoveVelocity;
	State			: INT := 0;
END_VAR
```

8. At "state = 0" the CASE function will run a code block. Power is enabled though first case, To power our axis, we use:

```
0:
ExAxPower.Enable := TRUE; //General software enable for the axis.
ExAxPower.Enable_Positive := TRUE; //Feed enable in positive direction.
ExAxPower.Enable_Negative := TRUE; //Feed enable in negative direction.
```

9. State is set to 1, in first caste for execution of futher code blocks in case function.
10.  In next step, Check whether the power is enabled, if it is uptate state integer to 2, using 
```
1:
IF ExAxPower.Active THEN
	state=2;
```

11. Put a cond


