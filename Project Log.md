I used this guide: https://learn.sparkfun.com/tutorials/hookup-guide-for-the-sparkfun-redboard-artemis-nano 

It has a lot of useful info.

Note: I am using Windows 10, so this Log will reference the relevant Windows 10 IDE links that I found useful. 

This project is technically a log, but I edit it occasionally so that it reads like a tutorial. 

This is because I try to make it easier to follow, to document the things that may have been missing or outdated in the original tutorials. 

It is always fun to be able to learn something difficult (to me) and to hopefully make it even easier to learn for others.
 
Fortunately, I did not have to buy a USB to Serial cable- this board has a CH340E chip, which has built in USB to Serial IC (https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)

so I can use any USB-C to USB-A to my PC. 

In my case, I  used a micro B USB adapter  https://www.adafruit.com/product/4299 which does the trick too.  

I was afraid my USB-C cables had more current so with this at least it won't be more than 5V.

I also have a Powerjive Usb Voltage/Amps Power Meter Tester Multimeter https://www.amazon.com/gp/product/B013FANC9W 

It is displaying 301mAh and 4.95V, with PWR (red LED), CHG (yellow LED) and bluetooth (blue LED) which normally blinks.

Not sure about that yellow light, but I will monitor it. 

I read somewhere it switches to 300mA if it receieves too much current? The yellow light isn't on all the time. Now the yellow light is off (after about 40 minutes).

Installed Arduino IDE 

Installed Putty

Installed https://www.wch.cn/downloads/CH341SER_EXE.html 

![USB-Serial CH340 - COM3](https://user-images.githubusercontent.com/76194453/203090524-c6f2764a-8bbf-4cea-b5ac-d92d8e2326f2.PNG)


The device manager shows the USB installed with the correct VID 0x1A86:

![image](https://user-images.githubusercontent.com/76194453/203091125-bce6d4ee-8664-47f5-92ca-6530b9cedf5c.png)

Setting up Arduino IDE

From SparkFun website:

"Note: The Arduino core for the Apollo3 (i.e. the board definitions) is only compatible up to release 1.8.12." 

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/setting-up-the-arduino-ide

I will go with the 1.8.12. (I hadn't realized I already Installed 2.0.2 already, but oh well, I have space for 2).
https://www.arduino.cc/en/software/OldSoftwareReleases#previous 
https://docs.arduino.cc/learn/starting-guide/cores

https://downloads.arduino.cc/arduino-1.8.12-windows.exe 

When prompted if I wanted to install a new version of Arduino, I selected "No" (since the Sparkfun page  hasn't been updated regarding compatibility for newer IDES for the Apollo3).

(some links from the above Sparkfun link is broken, such as "Installing Additional Cores", which points to:
https://www.arduino.cc/en/Guide/cores so I have found updated tutorials, such as: 
https://support.arduino.cc/hc/en-us/articles/360016466340-Add-or-remove-third-party-boards-in-Boards-Manager

That page also matches the UI of 1.8.12, and I was able to find Additional Boards Manager URLs under File: Preferences as stated. I then added the URL:

https://raw.githubusercontent.com/sparkfun/Arduino_Apollo3/main/package_sparkfun_apollo3_index.json

Now Apollo3 Boards appears under Boards Manager:
![image](https://user-images.githubusercontent.com/76194453/203129808-e2ae85dc-b664-480e-97dd-a6e69b120b1d.png)


One of the pictured links - "Online Help" redirects to: https://learn.sparkfun.com/tutorials/installing-arduino-ide/board-add-ons-with-arduino-board-manager
I also have a newer version than the pictured 2.0.0 in the Sparkfun tutorial. There are no compatibility issues mentioned, so I will just install the newest version (needs at least 2.0.0, according to Sparkfun page).

The "More Info" links to the SparkFun homepage. 

