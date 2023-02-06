1. Open TwinCAT and create a new project or open an existing one.

2. In the TwinCAT System Manager, right-click on the "Programs" folder and select "Add New Item".

3. In the "Add New Item" window, select "Global Variable" and click "Add".

4. In the "Create Global Variable" window, select the "User Type" tab and create a new user type with the name "MOUSEINPUT".

5. In the "MOUSEINPUT" user type, add the following variables:

Xpos: Integer  <br>
Ypos: Integer  <br>
LeftButton: Boolean <br>
RightButton: Boolean <br>
MiddleButton: Boolean <br>

5. Save the user type and close the window.

6. In the "Programs" folder, right-click and select "Add New Item" again.

7. In the "Add New Item" window, select "Program" and click "Add".

7. In the newly created program, declare a variable of the "MOUSEINPUT" type:

VAR MouseInput : MOUSEINPUT;

8. Use the following code to initialize and retrieve the mouse input:

Possible to use Windows API calls to retrieve mouse input, for example:

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

9. Start the program and the mouse input values will be updated in the "MouseInput" variable.

10. Use the values in the "MouseInput" variable as needed in your TwinCAT program.




