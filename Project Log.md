I used this guide: https://learn.sparkfun.com/tutorials/hookup-guide-for-the-sparkfun-redboard-artemis-nano 

It has a lot of useful info. 

Fortunately, I did not have to buy a USB to Serial cable- this board has a CH340E chip, which has built in USB to Serial IC, so I can use any USB-C to USB-A to my PC. 

In my case, I  used a micro B USB adapter  https://www.adafruit.com/product/4299 which does the trick too.  

I was afraid my USB-C cables had more current so with this at least it won't be more than 5V.

I also have a Powerjive Usb Voltage/Amps Power Meter Tester Multimeterhttps://www.amazon.com/gp/product/B013FANC9W 

It is displaying 301mAh and 4.95V, with PWR (red LED), CHG (yellow LED) and bluetooth (blue LED).

Not sure about that yellow light, but I will monitor it. 

I read somewhere it switches to 300mA if it receieves too much. 

Installed Arduino IDE 

Installed Putty

Installed https://www.wch.cn/downloads/CH341SER_EXE.html 

![USB-Serial CH340 - COM3](https://user-images.githubusercontent.com/76194453/203090524-c6f2764a-8bbf-4cea-b5ac-d92d8e2326f2.PNG)

The device manager shows the USB installed with the correct VID 0x1A86:
![image](https://user-images.githubusercontent.com/76194453/203091125-bce6d4ee-8664-47f5-92ca-6530b9cedf5c.png)
