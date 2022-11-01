**Project 24：WiFi Station+AP Mode**

1.  **Introduction：**
    
    ESP32 has three different WiFi operating modes : Station mode，AP
    mode and AP+Station mode. All WiFi programming projects must be
    configured with WiFi operating mode before using WiFi, otherwise
    WiFi cannot be used. In this project, we will learn ESP32's WiFi
    Station+AP mode.

2.  **Components：**

<table>
<tbody>
<tr class="odd">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/729232b0c2d2c01984808289b222890c.png" style="width:1.8125in;height:0.86458in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5012-Keyestudio-ESP32-Learning-Kit-Basic-Edition-Python/master/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg" style="width:2.43681in;height:1.13472in" /></td>
</tr>
<tr class="even">
<td>USB Cable*1</td>
<td>ESP32*1</td>
</tr>
</tbody>
</table>

3.  **Project wiring：**

Connect the ESP32 to the USB port on your computer using a USB cable.

![](/media/53f17b0de2d98d4714e8fe9043a346ca.jpeg)

4.  **Component knowledge：**

**AP+Station mode:** In addition to AP mode and Station mode, ESP32 can
also use AP mode and Station mode at the same time. This mode contains
the functions of the previous two modes. Turn on ESP32's Station mode,
connect it to the router network, and it can communicate with the
Internet via the router. At the same time, turn on its AP mode to create
a hotspot network. Other WiFi devices can choose to connect to the
router network or the hotspot network to communicate with ESP32.

5.  **Project code：**

Codes used in this tutorial are saved in“4. Python Tutorial\\2. Python
Projects”. You can move the codes to any location. For example, we save
the codes in Disk(D) with the path of“D:\\2. Python Projects”.

![](/media/906b7d4391131929a6b0726f7f5bab30.png)

Open“Thonny”，click“This computer”→“D:”→“2. Python Projects”→“Project
24：WiFi Station+AP Mode”，and double left-click
“Project\_24\_WiFi\_Station+AP\_Mode.py”.

![](/media/3eabed817cf0befdffb24e8ad7b9c89e.png)

<table>
<tbody>
<tr class="odd">
<td><p>import network #Import network module.</p>
<p>ssidRouter = 'ChinaNet-2.4G-0DF0' #Enter the router name</p>
<p>passwordRouter = 'ChinaNet@233' #Enter the router password</p>
<p>ssidAP = 'ESP32_WiFi'#Enter the AP name</p>
<p>passwordAP = '12345678' #Enter the AP password</p>
<p>local_IP = '192.168.0.147'</p>
<p>gateway = '192.168.0.1'</p>
<p>subnet = '255.255.255.0'</p>
<p>dns = '8.8.8.8'</p>
<p>sta_if = network.WLAN(network.STA_IF)</p>
<p>ap_if = network.WLAN(network.AP_IF)</p>
<p>def STA_Setup(ssidRouter,passwordRouter):</p>
<p>print("Setting soft-STA ... ")</p>
<p>if not sta_if.isconnected():</p>
<p>print('connecting to',ssidRouter)</p>
<p>sta_if.active(True)</p>
<p>sta_if.connect(ssidRouter,passwordRouter)</p>
<p>while not sta_if.isconnected():</p>
<p>pass</p>
<p>print('Connected, IP address:', sta_if.ifconfig())</p>
<p>print("Setup End")</p>
<p>def AP_Setup(ssidAP,passwordAP):</p>
<p>ap_if.ifconfig([local_IP,gateway,subnet,dns])</p>
<p>print("Setting soft-AP ... ")</p>
<p>ap_if.config(essid=ssidAP,authmode=network.AUTH_WPA_WPA2_PSK, password=passwordAP)</p>
<p>ap_if.active(True)</p>
<p>print('Success, IP address:', ap_if.ifconfig())</p>
<p>print("Setup End\n")</p>
<p>try:</p>
<p>AP_Setup(ssidAP,passwordAP)</p>
<p>STA_Setup(ssidRouter,passwordRouter)</p>
<p>except:</p>
<p>sta_if.disconnect()</p>
<p>ap_if.idsconnect()</p></td>
</tr>
</tbody>
</table>

6.  **Project result：**

It is analogous to Project 35 and project 36. Before running the code,
you need to modify ssidRouter, passwordRouter, ssidAP and passwordAP
shown in the box of the illustration above.

After making sure that the code is modified correctly,
click![](/media/da852227207616ccd9aff28f19e02690.png)“Run current script” the code starts to be
executed and the“Shell”window of Thonny IDE will display as follows:

![](/media/e9a8140dd6d9bb7ff8135a2be4170bd5.png)

![](/media/4167b186f19363fe8d2b0656d83b1760.png)

Turn on the WiFi scanning function of your phone, and you can see the
ssidAP on ESP32.

![](/media/3e0ad895bea7f5100cc02a415adcace7.png)
