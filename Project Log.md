I used this guide: https://learn.sparkfun.com/tutorials/hookup-guide-for-the-sparkfun-redboard-artemis-nano 

It has a lot of useful info.

Note: I am using Windows 10, so this Log will reference the relevant Windows 10 IDE links that I found useful. 

This page is technically a log, but I edit it occasionally so that it reads like a tutorial. 

This is because I try to make it easier to follow, to document the things that may have been missing or outdated in the original tutorials. 

A *few* (not MANY) of the logs may appear out of order. This is because some links earlier in the log have been updated/juxtaposed with additional information/comments, and may reference newer knowledge/progress. 

I have decided not to move up some of the earlier log entries to avoid even more achronological confusion. 

Most of this reads chronologically, thus try to read it that way. If it doesn't make sense, just move on and it might later on. 

It is always fun to be able to learn something difficult (to me) and to hopefully make it even easier to learn for others -including myself!

It can be quite surprising how easy it is to forget how to do anything, hence tutorials can be invaluable.
 
Fortunately, I did not have to buy a USB to Serial cable- this board has a CH340E chip, which has built in USB to Serial IC (https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)

so I can use any USB-C to USB-A to my PC. 

In my case, I  used a micro B USB adapter  https://www.adafruit.com/product/4299 which does the trick too.  

I was afraid my USB-C cables had more current so with this at least it won't be more than 5V.

I also have a Powerjive Usb Voltage/Amps Power Meter Tester Multimeter https://www.amazon.com/gp/product/B013FANC9W 

It is displaying 301mAh and 4.95V, with PWR (red LED), CHG (yellow LED) and bluetooth (blue LED) which normally blinks.

Not sure about that yellow light, but I will monitor it. 

I read somewhere it switches to 300mA if it receieves too much current? The yellow light isn't on all the time. Now the yellow light is off (after about 40 minutes).

Installed Arduino IDE (Note: At this point I installed 2.0.2, but use 1.8.12- more on that later)

Installed Putty

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/do-i-need-drivers

Installed https://www.wch.cn/downloads/CH341SER_EXE.html 

![USB-Serial CH340 - COM3](https://user-images.githubusercontent.com/76194453/203090524-c6f2764a-8bbf-4cea-b5ac-d92d8e2326f2.PNG)


The device manager shows the USB installed with the correct VID 0x1A86:

![image](https://user-images.githubusercontent.com/76194453/203091125-bce6d4ee-8664-47f5-92ca-6530b9cedf5c.png)

Setting up Arduino IDE

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/setting-up-the-arduino-ide ( you can also use 
https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/all to view it as a single page)

From SparkFun website:

"Note: The Arduino core for the Apollo3 (i.e. the board definitions) is only compatible up to release 1.8.12." 

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

Arduino now displays the Sparkfun Artemis Nano in the menus:

![image](https://user-images.githubusercontent.com/76194453/203133047-b778b541-3999-4740-8e0a-9749ee47bc3b.png)

I also installed a library, IRMP, which can be used for sending IR and RF signals. I do not know if I will use it yet, but I found it after searching for Apollo, and it was the only result that appeared. It may have no use for a file server, but I will keep the library, possibly for another project.

"More Info" redirects to: https://github.com/IRMP-org/IRMP 3.6.1 is installed.
![image](https://user-images.githubusercontent.com/76194453/203133792-d7cc2086-fec6-4801-a558-1c293779818b.png)

Next is to 

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/all 
This page mentions: 

"Note: For first-time users, who have never programmed before and are looking to use the Arduino IDE, we recommend beginning with the SparkFun Inventor's Kit (SIK), which includes a simpler board like the Arduino Uno or SparkFun RedBoard and is designed to help users get started programming with the Arduino IDE."

I chose to skip the inventor's kit. While I do want to learn additional devices, and technically have not programmed (for microcontrollers at least)- I have the Redboard Artemis Nano so I have the basic components of testing whether I am able to upload a file server to the nano (PC/IDE, USB cable, and microcontroller).   

Installing the Bluetooth library
"Installing the BLE Library
For users interested in the BLE functionality of the Apollo3 and Artemis boards, we have provided full support to the Arduino BLE library. Additional details about the library can be referenced from the documentation provided by Arduino.

Users will need to install the Arduino BLE library to take advantage of that functionality; please use the guide below, to get started with installing the Arduino BLE library:"
https://github.com/arduino-libraries/ArduinoBLE


Next Page (these will be detailed in future edits, if applicable to the file system project and are convenient placeholders/references without having to search multiple pages and tabs):
https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/programming-the-artemis-module

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/status-led-blink

14:58 So I tried this, and followed it step by step, until I got to: "The last step is to program your board. Use the programming method associated with your board."

The page redirects to: https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide#programming-the-artemis-module which doesn't directly link to the programming instruction, but you will still need to click on it. 

The page should say, "Introduction" at the top. Then, you need to click on the right column under pages, and then you will see "Programming the Artemis Module." 

I have added the direct link: https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/programming-the-artemis-module

It should now show "Drag and Drop Method" under the Programming the Artemis Module.

Notice the difference in the two links? the first one has a hashtag (#) after the Arduino. The 2nd link has a forward slash "/". 

That is why it is not easy to find all the pages in the tutorial at first. 

For programming, I will use the USB method, as it doesn't require any additional chips or cables. 

I also ensure "Bootloader: SparkFun Variable Loader" is selected. Update: I will use the alternate method:

"Known Issue: With the latest v2.0.0 Apollo3 Arduino core, there is an issue uploading sketched using the SVL.

Users can use the ASB to workaround this issue; however, it is recommended that users be aware of that there seems to be some sort of issue when uploading with the Serial Monitor left open. Even though the upload completes successfully the program does not execute."

Edit: from: https://learn.sparkfun.com/tutorials/designing-with-the-sparkfun-artemis#programming
" Heads up! You will never damage or brick the Artemis but using the Ambiq Secure Bootloader tools will overwrite the SparkFun bootloader removing the faster upload abilities. We don't recommend using the Ambiq Secure Bootloader for general Arduino programming."

Ok, I will not use the ASB anymore. 

Hoping I didn't already overwrite the Sparkfun Variable Loader. 
They say it can't be bricked. 
So we'll see. 
I am following these tutorials to test whether any signal has been sent over the USB.

If I am able to see a programmed response, then I will move on to more advanced file system installs.

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/serial-port-hello-world-and-enabling-peripherals

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/adc-analogread

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/pwm-analogwrite

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/i2c-qwiic-oled-display

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/spi-bme680-environmental-sensor

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/bluetooth-led

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/what-about-interrupts 

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/troubleshooting-tips
I tried to load the pre-compiled binary from the tips but did not get it to run. I read somewhere that I need to use 2 drivers, so maybe I may be missing one. And also, maybe I should reconsider using one of my complete USB-c cables, rather than the adapters, perhaps because the serial connection could result in an error.

https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/resources-and-going-further

After several hours, the Artemis Nano is has a steady red light and blinking blue light.
I have not seen the yellow light since I plugged it in hours ago.
Update it only appears when I tug on the USB connection, which can cause an unstable current. 
Allowing the board to rest without frequent movement helps ensure it does not get a variable current.

According to Arduino IDE, I was able to upload sample code with Artemis SVL: 
![image](https://user-images.githubusercontent.com/76194453/203163576-f6587f4f-8085-425c-9927-73ab12c77505.png)

Progress! 393216 bytes is 384KB, suggesting it was able to read from the RAM and measure how much was used. 

After having no luck with testing "Hello World" nor "Blink", I ran the Apollo3 example "Serial," and appear to have received the first return response (if that is from the MCU):
![image](https://user-images.githubusercontent.com/76194453/203168331-5d24c3c8-9704-4ca5-bace-63419f09edd7.png)

17:52 After swapping the micro B USB adapter and Jive USB meter with a single cable, I re-tested the Artemis, and changed the blink duration from 1000 milliseconds to 9000 milliseconds, allowing a clearer determination of whether the code actually updated.

![image](https://user-images.githubusercontent.com/76194453/203181487-8f4fa81b-b825-4747-8392-eaa0d374146d.png)

And it was a success! I was able to change the intervals for blinking to a solid Blue LED for 9 seconds, then off for 9 seconds. Also, when the SVL Bootloader is uploading, the Artemis flashes the RX (receive) yellow quickly to indicate it is doing something (like the disk LED on a PC). The upload is 115960 bytes, so during most of the transfer, RX blinks to indicate Arduino IDE & USB cable is uploading to the MCU. Very faintly does the TX (sending to the PC) blink. It is like a light green, and only blinks at the beginning and end of the upload.Also the CHG blinked a few times too (I forget the color).

![image](https://user-images.githubusercontent.com/76194453/203181918-6e482f7e-e270-4aa7-9837-de76bedd8f5f.png)

Yay! I now replaced the single USB-C cable with the USB multi-meter and adapter, eliminating it from the possible causes of error. I also change the LED ON to 500ms and left the OFF LED to 9 seconds. 

This concludes the basic testing of the Artemis Nano. Now I will move on to exploring which filesystems can be ported. What ever it is, it will be over 9000.

Actually one more test. I wanted to see if Bluetooth works.

I tried to run Example 11 BLEAdvertise, but I forgot to install the Bluetooth library (which I read about earlier today):
![image](https://user-images.githubusercontent.com/76194453/203188585-7283f30f-67ee-4b99-b6ea-783c49ff21cf.png)

I typed bluetooth and got quite a few results. I am only going to install the LE type.
More Info: https://www.arduino.cc/reference/en/libraries/arduinoble/  

I also installed Arduino Blue (3rd result in picture, but I will test it some other time)
More info: https://sites.google.com/stonybrook.edu/arduinoble/ 

![image](https://user-images.githubusercontent.com/76194453/203188856-df6067f3-ed7f-4e9e-9a56-fcd5bb4fe413.png)


After installing the library and re-running the example, the Artemis advertised itself and my phone could see the signal:
![Screenshot_20221121-190806_2 (1)](https://user-images.githubusercontent.com/76194453/203190463-93650546-1646-43f4-b78b-999797584e1e.png)

I was not able to connect to it, although there aren't any services for it to do. May as well test some of the other Bluetooth examples.

