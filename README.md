1. Open TwinCAT and create a new project or open an existing one.

2. In the TwinCAT System Manager, right-click on the "Programs" folder and select "Add New Item".

3. In the "Add New Item" window, select "Global Variable" and click "Add".

4. In the "Create Global Variable" window, select the "User Type" tab and create a new user type with the name "MOUSEINPUT".

5. In the "MOUSEINPUT" user type, add the following variables:

Xpos: Integer
Ypos: Integer
LeftButton: Boolean
RightButton: Boolean
MiddleButton: Boolean
5. Save the user type and close the window.

6. In the "Programs" folder, right-click and select "Add New Item" again.

7. In the "Add New Item" window, select "Program" and click "Add".

7. In the newly created program, declare a variable of the "MOUSEINPUT" type:

VAR MouseInput : MOUSEINPUT;

8. Use the following code to initialize and retrieve the mouse input:

Possible to use Windows API calls to retrieve mouse input, for example:

FUNCTION MouseInputTask() : VOID
    VAR hWindow : HANDLE;
    VAR pt : POINT;
BEGIN
    hWindow := GetActiveWindow();
    IF hWindow <> 0 THEN
        GetCursorPos(pt);
        ScreenToClient(hWindow, pt);
        MouseInput.Xpos := pt.x;
        MouseInput.Ypos := pt.y;
        MouseInput.LeftButton := (GetKeyState(VK_LBUTTON) AND $8000) <> 0;
        MouseInput.RightButton := (GetKeyState(VK_RBUTTON) AND $8000) <> 0;
        MouseInput.MiddleButton := (GetKeyState(VK_MBUTTON) AND $8000) <> 0;
    END_IF
END_FUNCTION

9. Start the program and the mouse input values will be updated in the "MouseInput" variable.

10. Use the values in the "MouseInput" variable as needed in your TwinCAT program.




