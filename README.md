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

Adding Enum in TwimCAT: 
![image](https://user-images.githubusercontent.com/59726765/216983459-383912bc-74b6-40d1-94b3-3ec85d28aad7.png)






1. Open TwinCAT and create a new project or open an existing one.

2. In the TwinCAT System Manager, right-click on the "Programs" folder and select "Add New Item".

3. In the "Add New Item" window, select "Global Variable" and click "Add".

4. In the "Create Global Variable" window, select the "User Type" tab and create a new user type with the name "MOUSEINPUT".

5. In the "MOUSEINPUT" user type, add the following variables:
 <br>

<i>
Xpos: Integer  <br>
Ypos: Integer  <br>
LeftButton: Boolean <br>
RightButton: Boolean <br>
MiddleButton: Boolean <br></i>

6. Save the user type and close the window.

7. In the "Programs" folder, right-click and select "Add New Item" again.

8. In the "Add New Item" window, select "Program" and click "Add".

9. In the newly created program, declare a variable of the "MOUSEINPUT" type:

VAR MouseInput : MOUSEINPUT;

10. Use the following code to initialize and retrieve the mouse input:

Possible to use Windows API calls to retrieve mouse input, for example:
<i>
FUNCTION MouseInputTask() : VOID <br>
    VAR hWindow : HANDLE; <br>
    VAR pt : POINT; <br>
BEGIN <br>
    hWindow := GetActiveWindow(); <br>
    IF hWindow <> 0 THEN<br>
        GetCursorPos(pt);<br>
        ScreenToClient(hWindow, pt);<br>
        MouseInput.Xpos := pt.x; <br>
        MouseInput.Ypos := pt.y;<br>
        MouseInput.LeftButton := (GetKeyState(VK_LBUTTON) AND $8000) <> 0;<br>
        MouseInput.RightButton := (GetKeyState(VK_RBUTTON) AND $8000) <> 0;<br>
        MouseInput.MiddleButton := (GetKeyState(VK_MBUTTON) AND $8000) <> 0;<br>
    END_IF<br>
END_FUNCTION<br>
</i>
<br>

11. Start the program and the mouse input values will be updated in the "MouseInput" variable.
12. Use the values in the "MouseInput" variable as needed in your TwinCAT program.




