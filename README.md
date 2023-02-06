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




