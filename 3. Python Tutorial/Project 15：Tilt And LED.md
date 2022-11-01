**Project 15：Tilt And LED**

1.  **Introduction：**
    
    The ancients without electronic clock, so the hourglass are invented
    to measure time. The hourglass has a large capacity on both sides,
    and which is filled with fine sand on one side. What’s more, there
    is a small channel in the middle, which can make the hourglass stand
    upright , the side with fine sand is on the top. due to the effect
    of gravity,the fine sand will flow down through the channel to the
    other side of the hourglass. When the sand reaches the bottom, turn
    it upside down and record the number of times it has gone through
    the hourglass, therefore, the next day we can know the approximate
    time of the day by it. In this project, we will use ESP32 to control
    the tilt switch and LED lights to simulate an hourglass and make an
    electronic hourglass.

2.  **Components：**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:1.99236in;height:0.97292in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/36f15610f430e5d5138f4e4fb721c40f.png" style="width:1.27292in;height:0.71667in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/ef77f5a64c382157fc2dea21ec373fef.png" style="width:0.29514in;height:1.25903in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/da8a2a9d15baf7280966f3fdbb025a8c.png" style="width:0.26042in;height:1.16667in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Tilt Switch*1</td>
<td>Red LED*4</td>
<td>10Ω Resistor*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.59028in;height:1.44583in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/845d05a6108b1662b828610ba9dcb788.png" style="width:0.25833in;height:1.13681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:1.05903in;height:0.56667in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.8375in;height:0.83194in" /></td>
</tr>
<tr class="even">
<td>Breadboard*1</td>
<td>22Ω Resistor*4</td>
<td>USB Cable*1</td>
<td>Jumper Wires</td>
</tr>
</tbody>
</table>

3.  **Component knowledge：**

![](/media/8c40739f8e05f753f145420b421a0f47.png)

Tilt switch is also called digital switch. Inside is a metal ball that
can roll. The principle of rolling the metal ball to contact with the
conductive plate at the bottom, which is used to control the on and off
of the circuit. When it is a rolling ball tilt sensing switch with
single directional trigger, the tilt sensor is tilted toward the trigger
end (two gold-plated pin ends), the tilt switch is in a closed circuit
and the voltage at the analog port is about 5V(binary number is 1023),
In this way, the LED will light up. When the tilting switch is in
horizontal position or tilting to the other end, the tilting switch is
in open state the voltage of the analog port is about 0V (binary number
is 0), the LED will turn off. In the program, we judge the state of the
switch based on whether the voltage value of the analog port is greater
than 2.5V (binary number is 512).

The internal structure of the tilt switch is used here to illustrate how
it works, as shown below:

![](/media/bf8b10ad248ac939ac4ef96d02ed87c7.png)

**4. Wiring Diagram：**

![](/media/a46c0b8be898ba596308ce56993c26ba.png)

**Note:**

How to connect the LED

![](/media/f70404aa49540fd7aecae944c7c01f83.jpeg)

How to identify the 220Ω 5-band resistor and 10KΩ 5-band resistor

![](/media/55c0199544e9819328f6d5778f10d7d0.png)

![](/media/246cf3885dc837c458a28123885c9f7b.png)

5.  **Project code：**

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→“Project 15:
Tilt And LED”, and then double left-click
“Project\_15\_Tilt\_And\_LED.py”.

![](/media/46f2dc07c27c05b1c15a4f40f67ad12c.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin</p>
<p>import time</p>
<p>led1 = Pin(16, Pin.OUT) # create LED object from Pin 16,Set Pin 16 to output</p>
<p>led2 = Pin(17, Pin.OUT) # create LED object from Pin 17,Set Pin 17 to output</p>
<p>led3 = Pin(18, Pin.OUT) # create LED object from Pin 18,Set Pin 18 to output</p>
<p>led4 = Pin(19, Pin.OUT) # create LED object from Pin 19,Set Pin 19 to output</p>
<p>Tilt_Sensor = Pin(15,Pin.IN) #Create tilt object from Pin15,Set GP15 to input</p>
<p>while True:</p>
<p>if(Tilt_Sensor.value() == 0) : #when the value of tilt sensor is 0</p>
<p>led1.value(1) # led1 turn on</p>
<p>time.sleep_ms(200)#delay</p>
<p>led2.value(1) # led2 turn on</p>
<p>time.sleep_ms(200)#delay</p>
<p>led3.value(1) # led3 turn on</p>
<p>time.sleep_ms(200)#delay</p>
<p>led4.value(1) # led4 turn on</p>
<p>time.sleep_ms(200)#delay</p>
<p>else : #when the value of tilt sensor is 1</p>
<p>led4.value(0) # led4 turn off</p>
<p>time.sleep_ms(200)#delay</p>
<p>led3.value(0) # led3 turn off</p>
<p>time.sleep_ms(200)#delay</p>
<p>led2.value(0) # led2 turn off</p>
<p>time.sleep_ms(200)#delay</p>
<p>led1.value(0) # led1 turn off</p>
<p>time.sleep_ms(200)#delay</p></td>
</tr>
</tbody>
</table>

6.  **Project result：**
    
    Make sure the ESP32 has been connected to the computer,
    click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend” .

![](/media/98065fdbe202e7cecdee16a404cd3396.png)

Click ![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”, the code starts to be
executed and you'll see that when you tilt the breadboard to an angle,
the LEDs will light up one by one. When you turn the breadboard to the
original angle, the LEDs will turn off one by one. Like the hourglass,
the sand will leak out over time. Press“Ctrl+C”or click
![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend”to exit the program.

![](/media/f1a599de742e8c16fe40eade5b5a07a7.png)
