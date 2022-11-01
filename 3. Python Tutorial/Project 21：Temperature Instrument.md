**Project 21：Temperature Instrument**

1.  **Introduction：**
    
    Thermistor is a kind of resistor whose resistance depends on
    temperature changes, which is widely used in gardening, home alarm
    system and other devices. Therefore, we can use the feature to make
    a temperature instrument.

2.  **Components：**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/56053f7126905c6def63919c661d5c0a.jpeg" style="width:1.59722in;height:0.77986in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e380dd26e4825be9a768973802a55fe6.png" style="width:0.69306in;height:1.7in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/b45bb81bb3763377c63accce606ac5f2.png" style="width:0.25in;height:1.11597in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/b395b1cd2678f87b3a34dec15659efbc.png" style="width:0.22431in;height:1.00556in" /></td>
</tr>
<tr class="even">
<td>ESP32*1</td>
<td>Breadboard*1</td>
<td>Thermistor*1</td>
<td>10KΩResistor*1</td>
</tr>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/74ca4fa6d49dbd04de6a603c6e55a9ee.png" style="width:1.15347in;height:0.9625in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/9232141f8a3166a8a6cdd43b78edd4e3.png" style="width:1.52014in;height:0.73264in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/e9a8d050105397bb183512fb4ffdd2f6.png" style="width:1.10139in;height:1.03472in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/7dcbd02995be3c142b2f97df7f7c03ce.png" style="width:0.99028in;height:0.52986in" /></td>
</tr>
<tr class="even">
<td>M-F Dupont Wires</td>
<td>LCD 128X32 DOT*1</td>
<td>Jumper Wires</td>
<td>USB Cable*1</td>
</tr>
</tbody>
</table>

3.  **Component knowledge：**

**Thermistor:** A Thermistor is a temperature sensitive resistor. When
it senses a change in temperature, the resistance of the Thermistor will
change. We can take advantage of this characteristic by using a
Thermistor to detect temperature intensity. A Thermistor and its
electronic symbol are shown below:

![](/media/809b8634747fb295021f12e3b92b7894.png)

The relationship between resistance value and temperature of a
thermistor is：

**Where:**

**Rt** is the thermistor resistance under T2 temperature;

**R** is the nominal resistance of thermistor under T1 temperature;

**EXP\[n\]** is nth power of e;

**B** is for thermal index;

**T1, T2** is Kelvin temperature (absolute temperature). Kelvin
temperature=273.15 + Celsius temperature.

For the parameters of the Thermistor, we use: B=3950, R=10k, T1=25.

The circuit connection method of the Thermistor is similar to
photoresistor, as the following：

![](/media/b0f80e9bd350a8b7390a73756ac1ac8c.jpeg)

We can use the value measured by the ADC converter to obtain the
resistance value of Thermistor, and then we can use the formula to
obtain the temperature value.

Therefore, the temperature formula can be derived as:：

4.  **Read the value of the Thermistor：**
    
    First we will learn the thermistor to read the current ADC value,
    voltage value and temperature value and print them out. Please
    connect the wires according to the wiring diagram below：

![](/media/806fd81bf8a761b4ae1a638489c426ce.png)

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→“Project 21:
Temperature Instrument, and then double left-click
“Project\_21.1\_Read\_the\_thermistor\_analog\_value.py”.

![](/media/e32d812b77cef0444c2e8da06f08e15d.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin, ADC</p>
<p>import time</p>
<p>import math</p>
<p>#Set ADC</p>
<p>adc=ADC(Pin(36))</p>
<p>adc.atten(ADC.ATTN_11DB)</p>
<p>adc.width(ADC.WIDTH_12BIT)</p>
<p>try:</p>
<p>while True:</p>
<p>adcValue = adc.read()</p>
<p>voltage = adcValue / 4095 * 3.3</p>
<p>Rt = 10 * voltage / (3.3-voltage)</p>
<p>tempK = (1 / (1 / (273.15+25) + (math.log(Rt/10)) / 3950))</p>
<p>tempC = (tempK - 273.15)</p>
<p>print("ADC value:",adcValue," Voltage:",voltage,"V"," Temperature: ",tempC,"C");</p>
<p>time.sleep(1)</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

Make sure the ESP32 has been connected to the computer,
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend”.

![](/media/1a2640b8b9f1fce96524c896da2961f4.png)

Click ![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”, the code starts to be
executed and you'll see that the "Shell" window of Thonny IDE will
continuously display the thermistor's current ADC value、voltage value
and temperature value. Try pinching the thermistor with your index
finger and thumb (don't touch wires) for a while, and you will see the
temperature increase. Press“Ctrl+C”or
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend”to exit the program.

![](/media/bf6784fc198ad4c14d6d19c6a285c44d.png)

![](/media/77f18a9e099306cd7111d6b2df2b5eb6.png)

5.  **Wiring diagram of the temperature instrument：**

![](/media/5a437bfdcad012211e15cab54e35dad7.png)

6.  **Project code：**

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→“Project 21:
Temperature Instrument”. Select“lcd128\_32.py”and
“lcd128\_32\_fonts.py”，right-click your mouse to select“Upload to
/”，wait for“lcd128\_32.py”and“lcd128\_32\_fonts.py”to be uploaded to
ESP32，and double left-click“Project\_21.2\_Temperature\_Instrument.py”.

![](/media/0b458bf5a07ae22c77127889de38299d.png)

![](/media/1ee304515bbfd76ed5c6b43f5faa68c0.png)

![](/media/afb73866962ea1872eb297b935b1f370.png)

<table>
<tbody>
<tr class="odd">
<td><p>from machine import Pin, ADC, I2C</p>
<p>import machine</p>
<p>import time</p>
<p>import math</p>
<p>import lcd128_32_fonts</p>
<p>from lcd128_32 import lcd128_32</p>
<p>#Set ADC</p>
<p>adc=ADC(Pin(36))</p>
<p>adc.atten(ADC.ATTN_11DB)</p>
<p>adc.width(ADC.WIDTH_12BIT)</p>
<p>#i2c config</p>
<p>clock_pin = 22</p>
<p>data_pin = 21</p>
<p>bus = 0</p>
<p>i2c_addr = 0x3f</p>
<p>use_i2c = True</p>
<p>def scan_for_devices():</p>
<p>i2c = machine.I2C(bus,sda=machine.Pin(data_pin),scl=machine.Pin(clock_pin))</p>
<p>devices = i2c.scan()</p>
<p>if devices:</p>
<p>for d in devices:</p>
<p>print(hex(d))</p>
<p>else:</p>
<p>print('no i2c devices')</p>
<p>try:</p>
<p>while True:</p>
<p>adcValue = adc.read()</p>
<p>voltage = adcValue / 4095 * 3.3</p>
<p>Rt = 10 * voltage / (3.3-voltage)</p>
<p>tempK = (1 / (1 / (273.15+25) + (math.log(Rt/10)) / 3950))</p>
<p>tempC = int(tempK - 273.15)</p>
<p>if use_i2c:</p>
<p>scan_for_devices()</p>
<p>lcd = lcd128_32(data_pin, clock_pin, bus, i2c_addr)</p>
<p>lcd.Clear()</p>
<p>lcd.Cursor(0, 0)</p>
<p>lcd.Display("Voltage:")</p>
<p>lcd.Cursor(0, 8)</p>
<p>lcd.Display(str(voltage))</p>
<p>lcd.Cursor(0, 20)</p>
<p>lcd.Display("V")</p>
<p>lcd.Cursor(2, 0)</p>
<p>lcd.Display("Temperature:")</p>
<p>lcd.Cursor(2, 12)</p>
<p>lcd.Display(str(tempC))</p>
<p>lcd.Cursor(2, 15)</p>
<p>lcd.Display("C")</p>
<p>time.sleep(0.5)</p>
<p>except:</p>
<p>pass</p></td>
</tr>
</tbody>
</table>

7.  **Project result：**

Make sure the ESP32 has been connected to the computer,
click![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart backend” .

![](/media/7ae58a587bde7630add8f5a3fca67eac.png)

Click ![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script”, the code starts to be
executed and you'll see that the LCD 128X32 DOT displays the voltage
value of the thermistor and the temperature value in the current
environment. Press“Ctrl+C”or click ![](/media/27451c8a9c13e29d02bc0f5831cfaf1f.png)“Stop/Restart
backend”to exit the program.

![](/media/fee11642c263c9f8b9549f96e384a5e0.png)
