**Project 20：Night Lamp**

1.  **Introduction：**

Sensors or components are ubiquitous in our daily life. For example,
some public street lamps will automatically turn on at night and turn
off during the day. Why? In fact, this make use of a photosensitive
element that senses the intensity of external ambient light. When the
outdoor brightness decreases at night, the street lights will turn on
automatically; In the daytime, the street lights will automatically turn
off. the principle of which is very simple, In this Project, we use
ESP32 to control a LED to achieve the effect of the street light.

2.  **Components：**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/d8beaf7391033a5f6ba4600791f8c348.jpeg" style="width:1.38681in;height:0.67708in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.6in;height:1.47083in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/ef77f5a64c382157fc2dea21ec373fef.png" style="width:0.29514in;height:1.25903in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/b395b1cd2678f87b3a34dec15659efbc.png" style="width:0.22431in;height:1.00556in" /></td>
<td></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Red LED*1</td>
<td>10KΩResistor*1</td>
<td></td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/9e553e75b6f976f33438171eb2f2e775.png" style="width:0.19097in;height:1.26597in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/845d05a6108b1662b828610ba9dcb788.png" style="width:0.25833in;height:1.13681in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:0.77222in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
<td></td>
</tr>
<tr class="even">
<td>Photoresistor*1</td>
<td>220ΩResistor*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
<td></td>
</tr>
</tbody>
</table>

3.  **Component knowledge：**

![](/media/9e553e75b6f976f33438171eb2f2e775.png)

**Photoresistor :** It is a kind of photosensitive resistance, its
principle is that the photoresistor surface receives brightness (light)
to reduce the resistance, the resistance value will change with the
detected intensity of the ambient light . With this characteristic, we
can use the photosensitive resistance to detect the light intensity.
Photosensitive resistance and its electronic symbol are as follows：

![](/media/7d575da675a2f6cb511d28b801e2abaa.png)

The following circuit is used to detect changes in resistance values of
photoresistors：

![](/media/5a7f7e641eb78007760a94151c1d80a5.png)

In the circuit above, when the resistance of the photoresistor changes
due to the change of light intensity, the voltage between the
photoresistor and resistance R2 will also change.  Thus, the intensity
of light can be obtained by measuring this voltage.

4.  **Read the ADC value, DAC value and voltage value of the
    photoresistor：**

We first use a simple code to read the ADC value, DAC value and voltage
value of the photoresistor and print them out. Please refer to the
following wiring diagram：

![](/media/b762098c798beb08e4d433137c317dc7.png)

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→”Project 20:
Night Lamp”，and then double left-click
“Project\_20.1\_Read\_Photosensitive\_Analog\_Value.py””.

![](/media/020a674603f00725d7e90ac42191254b.png)

<table>
<tbody>
<tr class="odd">
<td><p># Import Pin, ADC and DAC modules.</p>
<p>from machine import ADC,Pin,DAC</p>
<p>import time</p>
<p># Turn on and configure the ADC with the range of 0-3.3V</p>
<p>adc=ADC(Pin(36))</p>
<p>adc.atten(ADC.ATTN_11DB)</p>
<p>adc.width(ADC.WIDTH_12BIT)</p>
<p># Read ADC value once every 0.1seconds, convert ADC value to DAC value and output it,</p>
<p># and print these data to “Shell”.</p>
<p>try:</p>
<p>while True:</p>
<p>adcVal=adc.read()</p>
<p>dacVal=adcVal//16</p>
<p>voltage = adcVal / 4095.0 * 3.3</p>
<p>print("ADC Val:",adcVal,"DACVal:",dacVal,"Voltage:",voltage,"V")</p>
<p>time.sleep(0.1)</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

Make sure the ESP32 has been connected to the computer,
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend” .

![](/media/44a52e9513454de6e4aa3c081c053406.png)

Click![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”, the code starts to be
executed and you'll see that the "Shell" window of Thonny IDE will print
the ADC value、DAC value and voltage value of the photoresistor. When the
light intensity around the photoresistor is gradually reduced, the ADC
value、DAC value and voltage value will gradually increase. On the
contrary, the ADC value, DAC value and voltage value decreases
gradually. Press“Ctrl+C”or click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart
backend”to exit the program.

![](/media/2800cba7e9bea4354a779ac5056321f6.png)

![](/media/3b141ec51733d34caff4f0b2afc653a4.png)

5.  **Wiring diagram of the light-controlled lamp：**

We made a small dimming lamp in the front, now we will make a light
controlled lamp. The principle is the same, that is, the ESP32 takes the
ADC value of the sensor, and then adjusts the brightness of the LED.

![](/media/77a0c534501f51e7fe7aa221e4db71d9.png)

6.  **Project code：**

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→”Project 20:
Night Lamp”，and then double left-click “Project\_20.2\_Night\_Lamp.py”.

![](/media/aaf395f05aed9e464f97a2352429f813.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin,PWM,ADC</p>
<p>import time</p>
<p>pwm =PWM(Pin(15,Pin.OUT),1000)</p>
<p>adc=ADC(Pin(36))</p>
<p>adc.atten(ADC.ATTN_11DB)</p>
<p>adc.width(ADC.WIDTH_10BIT)</p>
<p>try:</p>
<p>while True:</p>
<p>adcValue=adc.read()</p>
<p>pwm.duty(adcValue)</p>
<p>print(adc.read())</p>
<p>time.sleep_ms(100)</p>
<p>except:</p>
<p>pwm.deinit()</p></td>
</tr>
</tbody>
</table>

7.  **Project result：**

Make sure the ESP32 has been connected to the computer,
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend” .

![](/media/faed424620c81b5ec6ab064926bd8b2a.png)

Click ![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”, the code starts to be
executed and you'll see that when the intensity of light around the
photoresistor is reduced, the LED will be bright, on the contrary, the
LED will be dim. Press“Ctrl+C”or
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend”to exit the program.

![](/media/fe8e8d7d176da2c1580ce74157775cd8.png)
