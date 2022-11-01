## Project 01: Hello World

1.  **Overview**

For ESP32 beginners, we will start with some simple things. In this
project, you only need a ESP32 mainboard, a USB cable and Raspberry Pi
to complete the "Hello World\!" project, which is a test of
communication between the ESP32 mainboard and the Raspberry Pi as well
as a primary project.

2.  **Components**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:1.56875in;height:0.76528in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/3bdcc62cfa661d2b860a76e28537e21e.png" style="width:1.41667in;height:0.76042in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Wiring Diagram：**

In this project, we will use a USB cable to connect the ESP32 to
Raspberry Pi.

![](/media/56053f7126905c6def63919c661d5c0a.jpeg)

**Running code online：**

To run the ESP32 online, you need to connect the ESP32 to the computer,
which allows you to compile or debug programs using Thonny software.  

Advantages:

1\. You can use the Thonny software to compile or debug programs.

2.Through the "Shell" window, you can view error messages and output
results generated during the running of the program as well as query
related function information online to help improve the program.  

Disadvantages:

1.  To run the ESP32 online, you must connect the ESP32 to a computer
    and run it with the Thonny software.  

<!-- end list -->

2.  If the ESP32 is disconnected from the computer , when they
    reconnect, the program won't run again.  

Basic Operation:

1.  Open Thonny and click“Open...”.
    
    ![](/media/319b34bcc43d038d633af9acba0c198c.png)

2.  Click“This computer”in the new pop-up window.
    
    ![](/media/5bdbc66ef89b41a53e46696c07b2c282.png)

In the new dialog box，select“Project\_01\_HelloWorld.py”,click“Open”.
The code used in this tutorial is saved in the file **4. Python
Tutorial\\2. Python Projects**. You can move the code to anywhere, for
example, we can save the **Python Projects in the** Disk(D), the route
is **D:\\2. Python Projects.**（The code in this tutorial is saved in the
Disk(D) on your computer）

![](/media/9b61f563870ec1235e6cc48ca748cec5.png)

3.  Click![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”to execute the
    program“Hello World\!”, "Welcome Keyestudio" , which will be printed
    in the“Shell”window.
    
    ![](/media/167c0dd1c25107701cb9c162a28d1f5e.png)

**Exit running online**

When running online, click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png) “Stop /Restart
Backend”or press “Ctrl+C”on the Thonny to exit the program.  

![](/media/dc2a210535724a7d601b5ad8b02ca8ed.png)

**5. Test Code**

<table>
<tbody>
<tr class="odd">
<td><p>print("Hello World!")</p>
<p>print("Welcome Keyestudio")</p></td>
</tr>
</tbody>
</table>
