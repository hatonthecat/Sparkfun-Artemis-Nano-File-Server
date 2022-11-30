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

Installed Arduino IDE (Note: At this point I already installed 2.0.2, but use 1.8.12- more on that later) (update 11-22: 2.0.2 has at least some limited functionality with the Artemis board)

Installed PuTTY

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

I chose to skip the inventor's kit. While I do want to learn additional devices, and technically have not programmed (for microcontrollers at least)- I have the Redboard Artemis Nano so I have the core components of the kit  to test whether I am able to upload data, and later, a file server to the Nano (PC/IDE, USB cable, and microcontroller).   

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

I was not able to connect to it, although there aren't any services for it to do. May as well test some of the other Bluetooth examples. After testing Advertising from ArduinoBLE->Peripheral, I got another SSID but still no connection. It said the error was PIN-related, but there was no prompt for one.

![Screenshot_20221121-192206_2](https://user-images.githubusercontent.com/76194453/203192425-665aeade-200b-4d3c-82ab-546a25ca7207.png)

Another Test- Example04_Serial:

![image](https://user-images.githubusercontent.com/76194453/203211994-baaf0072-1b30-4318-a2b5-3befb655c843.png)

And another: example10_DisplayICRevision:

![image](https://user-images.githubusercontent.com/76194453/203212416-6abdb504-4639-44fe-8194-27e1527e77ed.png)

For reference, previous Serial Monitor had no spaces because it was set to "no line ending." The NL & CR is for New Line and Carriage Return (like a typewriter; lines 2-4 are with NL& CR):
![image](https://user-images.githubusercontent.com/76194453/203212833-f810fa4f-8bc4-49ab-abb1-0299c29adc5c.png)

I am not sure how carriage return works- it does not create a new line after an arbitrary number of characters. 
Perhaps I have not tried enough characters. Not a major issue. I would recommend at least using New line for cleaner reading. 
Note: enabling timestamp without enabling New Line does not update the timestamp of each new character. 
So, to see the timestamp of each new character, "New Line" needs to be enabled as well.

And Another: i2c_readwrite by Adafruit.
![image](https://user-images.githubusercontent.com/76194453/203217539-dc5bbc33-5fd5-4c84-874b-98b9edcb70f6.png)

It did not find an address, but that could be because the Artemis Nano has i2c at a different address. 

Perhaps I can change the i2c address in this example to the one on the Sparkfun? Assuming the address for i2c were as simple as zero by two digits, it would still take some time to locate in the 900 page datasheet. I will pass for now. The UART pad mapping in Example 4 looks like shortcut, but still could be using different interfaces.


Just for fun

I tried to install LittleFS from ESP8266 using these instructions:

https://github.com/earlephilhower/arduino-esp8266littlefs-plugin 

It was a long shot, and needful to say, it didn't work:

![image](https://user-images.githubusercontent.com/76194453/203200510-11b1601e-46dc-4db2-9c46-4478a2c84116.png)

No worry, I can try another.  

I will return to Gemini servers at a later time (LittleFS was used in this ESP8266 Gemini Server:

https://github.com/w84death/ESP8266GeminiServer )

Micropython is used in PICO Gopher: 

https://github.com/aittalam/PicoGopher#running-the-code 

Is there a way this code could be used on Artemis?

I will find out.

----------------
----------------
||  DAY TWO  ||
----------------
----------------

08:24 AM

Returning to one of the things mentioned in the log yesterday - bootloaders - I want to "briefly" (Edit: I ended up writing not so briefly) examine why it was a good idea to start with the Sparkfun Variable Bootloader to test functionality (read: signal responses such as LED programming) of the Sparkfun Artemis Redboard Nano, and why, after just one day, I'm already looking for reasons to use the Ambiq Secure Bootloader.

First, a bit of background. I'm in my late-30s. Prior to yesterday, I have never attempted to program a microcontroller. I have, however, installed thousands, if not tens of thousands, linux and windows (and a handful of PowerPC MaC) operating systems in over 25 years, from Windows 95 on. My youtube channel has a few "boot linux from RAM" videos: https://youtu.be/MMFIzx3Cm9Q 

So in between, "I'm a middle-aged newb to MCUs" and "I know what I'm doing" (see Sparkfun's highly reccomended instructions, for newbs): 

![image](https://user-images.githubusercontent.com/76194453/203342279-72469f47-b846-4fb6-bce4-7440a4f16c1d.png)

above ^ from https://learn.sparkfun.com/tutorials/artemis-development-with-the-arduino-ide/programming-the-artemis-module

is a vast gray moon in between Venus and Mars that orbits neither of those two planets. (Granted, I am someone who has to ask myself, "am I a newb?" because I feel I am occasionally susceptible to the inferiority complex syndrome https://en.wikipedia.org/wiki/Inferiority_complex ) If you don't have that problem, at the other end of the scale, is the https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect There is also the Peter Principle and a few other ones that are somewhat in between. Perhaps I am unable to distinguish between hobby and professional skill because the exercise of learning can be so enjoyable. But of course, if one isn't being paid or doesn't feel they have a duty to develop a software for the common good, then the need to build secure and stable software may appear less of a priority. It isn't for me, but I sometimes forget how academic/experimental software can be. It's a learning experiment for the programmer, not just for a specific software, but for programming in general. I occupy a weird space of the hacker/maker/hobbyist tinkerer/post-baccalaureate autodidact continuum. 

In other words, I don't know <i>exactly</i> what I'm doing, but I know enough that I do probably will not need/do not want to use the Sparkfun Variable Bootloader soon, because some future OS/software may need a different bootloader. The Unknown or Bust (The Unknown may also bust/brick:). Known Knowns. Check. Known Unknowns. Check.  

Practically anyone with a tiny bit of experience need not rely on a single bootloader. 
Since the ultimate goal of this project is to install a filesystem, in any way possible, the bootloader is not a priority. It's like having a Windows bootloader instead of the GRUB bootloader. 
This is different from the newer WSL (Windows Subsystem for Linux). 
I am referring to whether the bootloader, which can allow multiple operating systems to be loaded without flashing the disk/ROM, is Windows-based or linux based. 
In most cases, the issue is minor- for a newb.

In other cases, for intermediate users, and experts, it makes all the difference. 

First, bootloader menus are often a temporary install for those who test operating systems. Yes, they can be permanent when used in production (or a final product), but for testing microcontrollers, having access to another bootloader is a tool. 
Sure, they are convenient, and sometimes can be skipped entirely- they serve a diagnostic and repair function, but there is always an intrinsic ability to erase a bootloader with another bootloader, provided the disk is not corrupt. 
That is where the user comes in. As a user/programmer, you are the person interfacing with the computer, therefore you have many choices on how to program and load not just software but operating systems.
The most visible difference with microcontrollers (and some system on a chips like the Rock Pi S https://www.perl.com/article/the-rock-pi-s-or-how-to-get-gpio-input-without-a-library/ ) and PC motherboards is that they do not have a convenient display connector like HDMI/VGA to see the bootloader screen immediately after installing software or an OS. 
Hence, why microcontrollers, and even other hardware use what's called, an "integrated development environment" or "IDE."

I haven't really had an interest in programming anything until I had a more concrete idea how i could go about developing what I want to do. 
I wouldn't expect anyone to. Programming is an abstact concept that relies on abstract languages to perform at often abstract layers. 
But is is a language, nonetheless, much like I am using expository techniques to provide a high-level overview of the reasoning of this project. 
I certainly could try to write a program with just machine/assembly language, but that is beyond my expertise. 
It certainly could be a useful application, and many are. 
But the language cannot easily be explained to someone who may not know computers, or even higher level languages. 

Anyways, the IDE exists for microcontrollers because their hardware, unless it has some kind of wireless connectivity, is basically on life support to the PC (for the purposes of interfacing and querying things on it). It is using a USB-serial debugger cable- in my case, a standard USB-C with an onboard CH340E IC, which converts the USB data from the PC's IDE software into code the microcontroller can use. So the IDE serves multiple functions here. It is used for programming new MCU software, but is also used for sending the data to the microcontroller- hence "integrated."

By contrast, there may be other discrete software applications for MCUs. I will not explore those right now. My point is that with Windows and Linux operating sytems, there are software such as image writers. The Raspberry Pi Imager is a GREAT one. It has the uncanny ability of fixing drives that cannot be recognized by Windows nor their size (sometimes this is done intentionally to make the drive bootable, but I digress). Other image writers include UNetbootin and Balena Etcher. One quick bug/tricky aspect of Raspberry Pi Imager is that while it is writing to disk, Windows will display a prompt saying that a drive is not plugged in and instructs the user to plug in the drive. If you press "Ok" or "cancel" (even though the Imager has begun writing /verifying to disk), it will abort the writing process. Basically, you have to let the Imager complete its writing process and Ignore the arbitrary prompts. The imager can format drives that even the Windows partition manager doesn't appear to.

Having briefly "digressed" into my hobby of testing and exploring OSes, I present this worldview as reasoning as to why I view microcontrollers like malleable disks. "If all you have is a hammer, everything looks like a nail." Sorry MCUs, you seem so like application processors. But MCUs are routinely flashed with userspace operating systems, and the amount of processing power they have compared to even 10 years ago is all the more reason to explore porting more user-space applications (not just sensors) to them. So now I can explore how to format and bootload a microcontroller, and how I may want to use the Ambiq Secure bootloader to install something like Zephyr OS, or FreeRTOS.

Other OSes supported include Tock: https://github.com/tock/tock/tree/master/boards/apollo3/redboard_artemis_nano So I may try this. I am currently more concerned with the feature of a FS over the OS, but eventually both will become equally a priority. 

-------------------------
11:50AM - Added Glossary
-------------------------

I have added a Glossary of IoT Terms, which will be handy for my future IoT software: https://github.com/hatonthecat/Sparkfun-Artemis-Nano-File-Server/blob/main/IoT%20Glossary%20%26%20Exegesis.md

---------------------
08:34 PM
---------------------

I plugged in my Power Jive to the PC, and realized it was displaying 301mA even without the Sparkfun Artemis attached. So that number is clearly not representing the draw of the Redboard Nano. I suspected it wasn't actually correct, since it may not have that margin of error detection. 301mA would be nearly 1.5 watts, and not even my Raspberry Pi Zero uses that much.

It turns out I was reading from the 10 preset/saved readings on the lower screen. The top bar shows the actual amperage, but only has two 00s past the decimal point. Thus even if it were running at 0.004 Amps, that would be 4mA and it wouldn't round up to .01A (10mA). The Sparkfun uses anywhere from 1.88mA- 6-7mA from what I've read: 

https://forum.sparkfun.com/viewtopic.php?p=207655#p207655

https://forum.sparkfun.com/viewtopic.php?t=50789#:~:text=The%20Nano%20is%20a%20bit,(again%20while%20running%20Blink).

"The Nano is a bit different since it does not use the LM117 regulator and also has the battery charging circuit included. In my testing with 5V applied to VIN the Nano was consuming ~6-7mA and ~4mA with 3.3V provided directly to the 3.3V pin (again while running Blink)." 

I will check the Jive Meter while running the Bluetooth test. Perhaps it will hit the 5mA threshold, which might appear as 0.01 if it rounds up. (for a $10 USB multimeter, I have to say this would be quite a powerful instrument)

9:16 PM 

Somehow my USB didn't seem to be working, but then I realized when I booted up Arduino IDE 2.0.2, it defaulted to a different Artemis board, the Artemis Dev Kit, so it was freezing on the upload stage. Arduino 1.8.12 was recognizing the right board, but seems to still stall on the upload stage. Perhaps something was overwritten and the folders are not working (maybe I updated the libraries by mistake).
![image](https://user-images.githubusercontent.com/76194453/203465917-355689d1-dc3e-4af4-9b62-ff526b3f55aa.png)


After correcting it an eliminating the usual suspects (PowerJive), I replugged in the USB and re-ran the Bluetooth test. It works on some of my USB cables, so I suspect a few of my USB cables only provide power. It's amazing how much time I can spend on trying to recreate all the conditions that were working yesterday, that it's taking over an hour to complete a single test.

I am going to use 2.0.2 for now- it is the only version that is able to upload right now, and it conveniently displays a message on whether the Artemis Nano is actually connected when plugggd in (Arduino 1.8 does too, but differently). After testing Example 11 (BLEAdvertise.ino), I did not see the PowerJive reach 0.00A, suggesting even when the "Artemis" appeared on my Phone's Bluetooth list, it was not using 10mA (nor enough for the PowerJive to round up, if they even do that).

![image](https://user-images.githubusercontent.com/76194453/203467090-2b6297aa-397c-4108-9732-0e89be4fd42c.png)


So I will test the Blink test again, raising it to 20000 milliseconds, to perhaps notice a spike in power. I did not see any fluctuation of 0.01A- there are two LEDs, the Red and Blue, and while the Blue is very bright, it does not use 10mA. I will re-test the bluetooth example, because I was able to erase one of my presets that was in the thousands of millamps, since I clearly knew it was not from the Artemis Nano. Perhaps the preset does allow the PowerJive to reveal up to 4 decimal points, because while it does not appear on the top row, perhaps I can capture the measurement during the bluetooth test. Preset 0 shows 0000mA for the LED test, which may be inaccurate (probably), or doesn't have that sensitivity (though one of my presets appears as 0001mA.  

I ran the EnhancedAdvertising Test from ArduinoBLE.h it did not reach 10mA. Perhaps the "LE" is what makes it so low power. Kudos. I will try the ArduinoBlue test for multiple LED brightness.ino It appears the library isn't installed for SoftwareSerial.h. I will try another app, LED.ino and it says I can install a couple apps. LightBlue and and nRF Connect for Android. This is also from the ArduinoBLE Example (not from the ArduinoBlue). It wasn't able to connect, likely because the PIN wasn't registering. 

On checking the Sparkfun forums, there appears to be a working bluetooth example with the LightBlue app. Retesting it https://forum.sparkfun.com/viewtopic.php?p=210145#p210145 It didn't apear to work.

I have downloaded the Sparkfun Firmware Uploader GUI. https://github.com/sparkfun/Artemis-Firmware-Upload-GUI

Perhaps I am using an older version. I am also curious about this D19 1hz LED blinker. What Hz was it using before? I will wait on that. Instead I will try to burn the bootloader to ensure my uploads are not running too slow. They seem to work fine, though the compiling appears a little slow. https://learn.sparkfun.com/tutorials/designing-with-the-sparkfun-artemis/all#troubleshooting suggests I could reinstall the SVL. I may wait on this too. 

I ran the Firmware update. It changed the blinking to every other second. The first try didn't work, as I selected Bootloader first, out of order from the instructions. At 11:57PM, trying to follow instructions can sometimes be a best-effort.

"Updating bootloader

Artemis Bootloader Update

Installing bootloader version 5
Header Size = 0x80
original app_size 12940
load_address 0xc000
app_size 12940
w0 = 0xcb00330c
Security Value 0x10
w2 = 0x10008080
addrWord = 0xc000
versionKeyWord = 0x0
child0/feature = 0xffffffff
child1 = 0xffffffff
crc =  0xc703da31
Writing to file application_OTA_blob.bin
testing: application_OTA_blob.bin
Header Size = 0x60
app_size = 13068
Writing to file application_Wired_OTA_blob.bin
Image from 0x0 to 0x330c will be loaded at 0x20000
Connecting over serial port...
Sending Hello.
No response for command bytearray(b'\x00\x00\x08\x00')
received 62 bytes
Failed to respond
Fail
Sending Hello.
No response for command bytearray(b'\x00\x00\x08\x00')
received 62 bytes
Failed to respond
Fail
Sending Hello.
No response for command bytearray(b'\x00\x00\x08\x00')
received 62 bytes
Failed to respond
Fail
Tries = 3
Upload failed!

Uploading firmware

Artemis SVL Uploader

Phase:	Setup
	Cleared startup blip
	Got SVL Bootloader Version: 5
	Sending 'enter bootloader' command
Phase:	Bootload
	Sending 8784 bytes in 5 frames
	Got frame request
	Sending frame #1, length: 2048
	Got frame request
	Sending frame #2, length: 2048
	Got frame request
	Sending frame #3, length: 2048
	Got frame request
	Sending frame #4, length: 2048
	Got frame request
	Sending frame #5, length: 592
	Got frame request
Upload complete! "

I already have the latest version - 5 so I will not need to update it.

It's now 12:02 PM, so I will begin Day 3. Day 2 was not what I had planned- I was hoping to try out or port new software, but obviously that takes a lot of time, and running more simple tests with existing software for the library helps me get a better idea of capabilities. Since power consumption is so central to the design of an autarkic fileserver, it helps to know whether the device is using 12mW or 35mW (1.88mA x 4.95V, or 7mA x 4.95V as mentioned in the SparkFun forum. At 48mhz (fixed), the Artemis module is probably running 288uA (around 1.5mW, and the LEDs and radios are potentially using the rest of the power. Perhaps the PowerJive does not register 9mA as 0.01 A until it actually passes the 10mA (with a +/- 1mA margins). The page says 1% accuracy (although it was referring to voltage). this reviewer also could not get their device to be detected with an Adafruit microcontroller: https://www.amazon.com/gp/customer-reviews/R2S4LFQ7IEODUM

This is good news. In a way, I was expecting it to appear as 0.01A, but that would be only if it could not detect the difference between 7mA and 10mA (suggesting less than +/- 3% accuracy). And even if it could, the meter is probably not rounding up nor the Redboard is using that much. It might only be using 2-3mA, which suggests it's using no more than 15mW, on idle/low activity. There may be a way to disable the LEDs. Green LEDs use less power than Blue, and Red LEDs use the most power.

----------------
||  Day Three  ||
----------------

9:48 AM I hadn't realized I created an index by typing lines around Day 2, so I copied the format for Day 3. 

By index I'm referring to the three lines to the left of the revision bar: 

![image](https://user-images.githubusercontent.com/76194453/203590094-d7d40d07-3aee-43ee-81ac-df2698f4744b.png)
 
 I can probably shorten the lines and use fewer of them. Did you know, that most of the learning in programming is done by typing and testing things? Not just reading about things? Surely some read the user manual for Github before coding, but how many actually do that? I'm sure there are many tricks for editing a page with additional indents, but I am just concerned with occasional indexes separated by days, and unfortunately, I am not consistent with the format, so occasionally the index will show middle of the day line breaks. Sometimes it helps me more than the reader. 
 
9:55 AM It turns out I only need one line of dashed "-"s to create an indexed entry. I do use the preview option- it is actually quite convenient, but I make hundreds of commits anyways, to fix typos and other formatting issues. The # of commits in all my pages are hardly like other Github projects where they are adding code, so I realize people who view my contribution activity:

![image](https://user-images.githubusercontent.com/76194453/203593151-ce8f2e53-0aa8-4021-bb78-9172879cc9f6.png)


and see 156 commits in November, may think, wow this person is hard at work- I am not trying to create the appearance that I'm writing software -YET- I just have a lot of writing to do as well. I know it may look like that if viewing my profile, but I can assure you, if I focused too much on my appearance, I would never get anything done. Apologies if this looks more like a Wordpress entry.  

-----------
9:30 PM
------------

LittleFS for MbedOS. The Sparkfun Artemis supports MbedOS, so this version of LittleFS may work for the Artemis. some assembly required, I assume.
https://os.mbed.com/blog/entry/littlefs-high-integrity-embedded-fs/ 
https://github.com/ARMmbed/mbed-os/tree/master/storage/filesystem/littlefs
http://littlefs.geky.net/demo.html

One of the the inexplicable things a newb is tasked with is how software can actually be uploaded to a microcontroller to perform a function. Even if I uploaded a file system file, does the software have a way to check that it's there, via serial cable? I know I have to include some other program to use that file system, such as an httpd daemon. This is why microcontrollers are so foreign to me. With a linux operating sytem or windows, there is a software manager, synaptic, or .exe/.msi files, that intrinsically run when they are on the screen. Microcontrollers don't have this instant-acess option, not outside an IDE or a pre-installed peripheral I/O. So while MCUs aren't designed like PCs, that is still the only way I can understand them. Sure, they can operate as a sensor on 32KB. But this has 384KB. So the file system is far more interesting. Regrettably, I can't make this up. It's not a joke. I am trying to learn the ways of the MCU, but it's taking longer than expected.

9:54 PM How the Bluetooth talks with the MCU. 

This should be in a Microcontrollers & Wireless Communications 101 Course 

https://www.feasycom.com/bluetooth-host-controller-interface-hci.html
"The host controller interface (HCI) layer is a thin layer which transports commands and events between the host and controller elements of the Bluetooth protocol stack. In a pure network processor application, the HCI layer is implemented through a transport protocol such as SPI or UART.

HCI Interface
The communication between a Host (a computer or an MCU) and a Host Controller (the actual Bluetooth chipset) follows the Host Controller Interface (HCI).

HCI defines how commands, events, asynchronous and synchronous data packets are exchanged. Asynchronous packets (ACL) are used for data transfer, while synchronous packets (SCO) are used for Voice with the Headset and the Hands-Free Profiles."

Thank you Feasycom. I love when words like "actual" are used. It means the engineer writing the technical manual realizes the programmer understands a bluetooth device is somewhere on the integrated microcontroller chip (as many are SoCs now), and needs to specify that communication has to occur somehow. I need this kind of specificity, because abstractness between software and hardware is not clear enough. PCs have controllers for displays and all sorts of devices:

![image](https://user-images.githubusercontent.com/76194453/203691805-dd266852-f20c-498d-be05-126f6c260ab7.png)

https://en.wikipedia.org/wiki/List_of_Bluetooth_protocols#HCI Controllers are something I understand. I am going to need this sometime. 

More great references for the BLE beginner: https://pcng.medium.com/ble-protocol-stack-host-controller-interface-hci-44dd5697bd8

https://www.amd.e-technik.uni-rostock.de/ma/gol/lectures/wirlec/bluetooth_info/hci.html

What's this HAL? 

https://www.digikey.com/en/maker/projects/artemis-development-with-arduino/d38350a88bb74bd4a5c6e02bf493ece9

Not to be confused with HCI, HAL is another term I saw pop up yesterday and the day before. HAL is hardware abstraction layer. Another SDK, the Ambiq SDK, includes these examples and functions. 

"This is a powerful tool for advanced users; you can use the built in Arduino functions such as Serial.begin(9600) and delay(100) while integrating more advanced HAL functions for controlling things like interrupts."

I appreciate the heads up. But I will take anything I am offered. While technically I am a beginner, the wording of this explains more about the board than some beginner guides. I am not claiming I understand even 1% of advanced programming, I just needed to know this before I dive into beginner's tutorials. It's better to try to briefly provide a high-level overview of all the concepts of a microcontroller without assuming difficulty. I can usually find out more information when I need- such as interrupt parameters- perhaps why so many tutorials try to omit information like this is because they are too afraid of confusing the reader. Some learners are non-linear. From context, it sounds like I can mix some advanced functions with the pre-baked Arduino functions in the same Arduino enviroment, as long as write the code correctly. Am I right? See, you can graduate from beginner school in 3 days. I believe in you. Don't let anyone tell you something is purely advanced. Chances are, you deserve an attempt at an explanation at least. Tutorial books need to say what people can be capable of, so they have something to look forward to. Everything is for beginners, but no one wants to be stuck in the mindset that they are a beginner or patronized.

11:14 PM

https://os.mbed.com/docs/mbed-os/v6.15/apis/blockdevice-apis.html

So apparently some microcontrollers may not support all the development board OS features. This is another jarring difference between MCUs and PCs. Some MCUs don't appear to be able to be "just flashed" with an OS. They need to support the IDE that goes with it. And development boards only appear when I search Block device APIS supported, Artemis doesn't appear. I should write a book - Microcontrollers for the Layman. In the 90s, PCs used to have a sticker on them that they supported Windows 95 or 98. Is this so hard? In plain language, when  microcontroller is sold, it should say whether it supports an OS or not. Not some development environment with half the features. It may support all the features, but MCU hardware and software developers don't bother to explain it to people they never thought would even try to understand this stuff.

What am I referring to? This:

![image](https://user-images.githubusercontent.com/76194453/203700545-06a22f49-540d-40a3-a503-dad101f4ed80.png)

It seems so simple. I want to use this block API. At least I think I do. When I click on "Import into Mbed IDE" which I already have the desktop version, it redirects me to the web version, which is being deprecated in December 2022 for Keil

The soon to be deprecated: 

![image](https://user-images.githubusercontent.com/76194453/203700825-4fec6570-7cbb-4352-8e58-952f93183808.png)

A bit of good news: 

"Keil Studio Cloud is based on a modern IDE framework and gives Arm the opportunity to develop features that would not have been possible with the Online Compiler. Our codebase gives us the flexibility to deploy to the desktop (in the guise of Mbed Studio), or to the browser, or even as Visual Studio Code extensions in future."
https://os.mbed.com/blog/entry/keil-studio-cloud-mbed-online-compiler/

So I won't need to reinstall the desktop client when Keil launches next month after just installing Mbed Studio, like 2 days ago. Thanks! :)

Back to what I was saying, when I click Import into Mbed IDE, I get this popup:

![image](https://user-images.githubusercontent.com/76194453/203701381-5467c48c-e8d0-4225-b725-1cc98b72809d.png)


I haven't added a platform. Yes, it's true. I haven't added a platform. But something tells me it's not going to support my Artemis Nano, because it's not a development board like the $48 Sparkfun Artemis Development Kit: https://www.sparkfun.com/products/16828

You mean I can't just program something virtually in a desktop environment and then test the code on the Nano that I spent $15 for? What am I missing? Or rather, what is the board missing? Sigh... 

Even before filtering for Cortex M4 and BLE, there are no Sparkfun boards on the Mbed site:

![image](https://user-images.githubusercontent.com/76194453/203702210-8e6e0d2b-169c-4e8a-a3e8-0d011f6d7102.png)

You'd think ARM, which makes the MCU architecture/license, would want to include them on the site. Why not? Sparkfun has its own Mbed repository. But. Is it compatible with all the wonderful software that they talk about on the MbedOS site? No software should be left behind.

MbedOS for Sparkfun has been in Beta for over 2 years. Even if does support MbedOS, is anyone even still working on this? This board is one of the greatest microcontrollers I've seen. It's sad that there aren't more developers interested.

https://learn.sparkfun.com/tutorials/artemis-development-on-arm-mbed-os-beta/all 

https://github.com/sparkfun/mbed-os-ambiq-apollo3/tree/ambiq-apollo3-dev 

Oh wait, there is littleFS in this branch, but it hasn't been updated in nearly 2 years. It looks like someone did some refactor work: 
https://github.com/ARMmbed/mbed-os/pull/13433

By the way, I'm not really upset at any of the websites or developers. I just like narrating the chronological order when I fail to find something, and occasionally highlight overly technical landing pages which could have a simplified, semantic search and alternative home page for newbs like me.

-------------
Day 4
-------------

1:14 AM 

So it turns out there is some development still going on. I am just hesitant to peer into the SparkFun forums sometimes. Maybe because I fear what I will read about hardware deprecation.

https://forum.sparkfun.com/viewtopic.php?f=183&t=58462  The Sparkfun boards are running Mbed OS 5, not 6. 
https://github.com/paulvha/apollo3/tree/master/MBED-BLE
https://forum.sparkfun.com/viewtopic.php?f=170&t=58483

Are they talking about the same OLA as this? I had a similar idea in mind- once the file system is installed, then I'd interface with the BLE HCI
https://www.openlighting.org/ola/getting-started/using-ola/ 

I think my questions have been answered:
from: https://forum.sparkfun.com/viewtopic.php?p=236512#p236512
"Wed Oct 19, 2022 11:10 pm
Nothing. Sorry!

The hardware and Mbed OS both support BLE, but we just haven't had the time or resources to be able to add support in the OLA firmware. It's a big project and we have new hardware coming where it will be _much_ easier to support Bluetooth and WiFi connectivity."

New Hardware...Hmm, hopefully an Artemis with Apollo4, with MbedOS6 or anything that lets me program a lot of things, without needing a bunch of different libaries.- like one big library would be nice...

Well that makes sense.. wait for new hardware that fixes problems that would take too long to develop on older hardware. Seeing that there are only 6 Sparkfun developers on Github in the repository, it is clear there isn't a ton of resources to develop on a platform that is not going to be as popular as what's probably in the pipelines. Sure, I'd buy an Apollo4 with 2MB of RAM, but there is still a lot of potential on 384KB. But I'm not sure if it will be cost effective to develop for the Artemis with Apollo3 unless it is backward compatible (assuming it's even the same architecture).

------
Day 5 
------
10:54AM 
Thursday through Saturday was a holiday break, and I was out of town. Technically Day 7 from start date. I did get some Arduino links that may be of help- simulators that may be able to 
virtually run/test applications that I've wanted to build for the Artemis:

https://wokwi.com/ 

https://simulation.iitbx.in/arduino/

https://www.tinkercad.com/ I am not sure if these are hardware-centric or software- they seem to be hardware, but some software as well. 

The operating systems are of course important, but the ability to test code on the Artemis using the current IDE may suffice. Thus it's not clear if the IDE lets me send and build a filesystem/fileserver, or just instructions.

This is not related, but I may glean some concepts from the BBC Microbit: https://learn.sparkfun.com/tutorials/getting-started-with-the-microbit/all

1:03PM 

I have located another Sparkfun page confirming that all Artemis boards are fully MbedOS supported. https://www.sparkfun.com/news/3376
"Starting today, full Arduino IDE, Bluetooth 5.0, and Arm Mbed OS software support is provided with all Artemis boards!" I'm glad of this, and especially because focusing on one board is the best way to learn how to program. There is a lot to overlook, which is why a site can have many pages that aren't necessarily disorganized, but require time and patience to actually understand.

![image](https://user-images.githubusercontent.com/76194453/204154975-3396eca8-0e72-41c5-995a-11b6954feef9.png)
https://learn.sparkfun.com/tutorials/getting-started-with-the-artemis-development-kit Again, I appreciate this warning, but I will forge ahead.

" Recommended software to program the Artemis DK include the Arduino IDE, Arm® Mbed™ OS and AmbiqSDK. An updated USB interface (MKL26Z128VFM4 Arm® Cortex-M0+ MCU, from NXP) allows the Artemis Dev Kit to act as:

Mass Storage Device (MSD): provides drag-and-drop programming to the Artemis Module
Human Interface Device (HID): for the debugging interface to the Artemis Module
Communication Port (COM): provides a serial communication UART between the Artemis and the USB connection (PC)"

Not 100% sure I can drag and drop on my Nano board, but it seems like the Dev Kit board supports it.

https://learn.sparkfun.com/tutorials/artemis-development-on-arm-mbed-os-beta 

![image](https://user-images.githubusercontent.com/76194453/204156868-28e84c9e-518c-4c63-bdd8-13143ebf294e.png)

I had previously cloned the fork uding GitHub desktop. The only step I did not do is "pull the ambiq-apollo3-dev branch, as I'm not sure if it will try to propose changes (which I am not interested in, at least right now). 

I did pull Mbed OS full profile in MbedOS and

![image](https://user-images.githubusercontent.com/76194453/204156981-d62868a1-a6d2-4932-8e79-db485470cf62.png)

selected Blinky from Mbed OS 6.

I then selected Link to an existing shared MbedOS instance, finding the directory of my ambiq-apollo3-dev.

It is now active in MbedOS studio, however, I did notice it says "requires 6.13.0" :

![image](https://user-images.githubusercontent.com/76194453/204157100-7218a279-8474-40ac-9b54-5c805e2e7d19.png)


Which suggests the MbedOS 6 that I loaded is older than Mbed OS 6. I recall importing MBedOS 5 at some point, if i am not mistaken, so I may have to clone the newer version, first from Github, then link it to MbedOS. (Or just pull request?)

 2:12PM 
 
 I did set up a remote repository: 

![image](https://user-images.githubusercontent.com/76194453/204157452-e8f99a46-ae75-45dc-9a54-dd1cfa82be20.png)

However, I do not know if it downloaded the updated respository and corresponding MbedOS(probably not)

Useful resource (41 pages): https://media.digikey.com/pdf/Data%20Sheets/Sparkfun%20PDFs/Artemis_Development_Kit_Getting_Started_Web.pdf

Also, I learned there is a term for the USB programming method. It's called In-system programming:
https://en.wikipedia.org/wiki/In-system_programming 
"In-system programming (ISP), or also called in-circuit serial programming (ICSP), is the ability of some programmable logic devices, microcontrollers, and other embedded devices to be programmed while installed in a complete system, rather than requiring the chip to be programmed prior to installing it into the system. It also allows firmware updates to be delivered to the on-chip memory of microcontrollers and related processors without requiring specialist programming circuitry on the circuit board, and simplifies design work.[1]" This is a good background: https://www.oreilly.com/library/view/designing-embedded-hardware/0596007558/ch01.html I never knew how much background material I'd need. Back to the textbooks, I suppose.

Microcontrollers are computers, but I prefer to let the textbooks confirm that:
"In this chapter, we’ll look at computer architecture in general. This is applicable to both embedded and desktop computers, because the primary difference between an embedded machine and a general-purpose computer is its application. The basic principles of operation and the underlying architectures are fundamentally the same."

A number of websites describe this reality: https://jaycarlson.net/embedded-linux/

https://elinux.org/images/c/ca/Spreading.pdf 

"When your microcontroller project outgrows its super loop and the random ISRs you’ve sprinkled throughout your code with care, there are many bare-metal tasking kernels to turn to — FreeRTOS, ThreadX (now Azure RTOS), RT-Thread, μC/OS, etc. By an academic definition, these are operating systems. However, compared to Linux, it’s more useful to think of these as a framework you use to write your bare-metal application inside. They provide the core components of an operating system: threads (and obviously a scheduler), semaphores, message-passing, and events. Some of these also have networking, filesystems, and other libraries."

Although they do not all/always recommend running linux without an MMU:

"Responsiveness. By default, Linux’s scheduler and resource system are full of unbounded latencies that under weird and improbable scenarios may take a long time to resolve (or may actually never resolve). Have you ever seen your mouse lock up for 3 seconds randomly? There you go. If you’re building a ventilator with Linux, think carefully about that. To combat this, there’s been a PREEMPT_RT patch for some time that turns Linux into a real-time operating system with a scheduler that can basically preempt anything to make sure a hard-real-time task gets a chance to run.

Also, when many people think they need a hard-real-time kernel, they really just want their code to be low-jitter. Coming from Microcontrollerland, it feels like a 1000 MHz processor should be able to bit-bang something like a 50 kHz square wave consistently, but you would be wrong. The Linux scheduler is going to give you something on the order of ±10 µs of jitter for interrupts, not the ±10 ns jitter you’re used to on microcontrollers. This can be remedied too, though: while Linux gobbles up all the normal ARM interrupt vectors, it doesn’t touch FIQ, so you can write custom FIQ handlers that execute completely outside of kernel space."

Which prompts the question, "why not use something <i>like</i> linux, but not linux, on an MCU? Running applications in baremetal is an option- exokernel and SASOS can remove lots of the conveniences (and latencies) of OSes when the application is known (especially with low Mhz microcontrollers (targeting 100-200mhz, not 1000mhz). Other projects like https://github.com/embox/embox aim for the same goals- linux without linux. Some of the The RTOS aspects of the Symbian EKA2 kernel are a bonus for applications, as the main objective was to consolidate PMIC and signal stack into a single processor, to save on the bill of materials. Ideally, this kernel structure could be explored more for basic feature phones (read 1990s era) on the lightest microcontrollers.

4:38 PM

I did a test build:

![image](https://user-images.githubusercontent.com/76194453/204163540-17981228-ff1b-4bb7-a097-32b6d014ae5c.png)
(File this under "I don't know what I'm doing"- since it may just be built on the PC, but nothing transferred, for the better-for now)
Compared to the Instructions, which used the dev kit:
![image](https://user-images.githubusercontent.com/76194453/204163608-e96d427e-e621-4fc2-ba20-5d73d8bec586.png)

I selected Nano - but the "USB device" drop down didn't appear, and I may have used a different screen.
 
----------
Day 6
----------

10:58 AM Technically 9th day from start date.

I am cross-linking this with the GEOS project- as I'd like to explore emulating 8bit-GEOS: https://github.com/hatonthecat/ENGAGE-GEOS

2:15PM I learned a new IC driver: FT232: https://www.adafruit.com/product/2264

It's like IC, but adds additional functions: "What can the FT232H chip do?  This chip from FTDI is similar to their USB to serial converter chips but adds a 'multi-protocol synchronous serial engine' which allows it to speak many common protocols like SPI, I2C, serial UART, JTAG, and more!"

Wait, so I don't really need CH340?. Something tells me this board interacts with boards, apparently through the 3-pin 3V power input. But I am assuming the power input doubles as an analog signal, which converts the FT232 board's data from the PC to the target board. Apparently it's only for Stemma products, but I'm aware that power cables can be used as a piggyback for data (after all, isn't USB-C/micro-USB the same?).

10:21 PM: Some new OSes I've found for the Rpi Pico include a filesystem https://git.kj7rrv.com/kj7rrv/fibonaccios (These are considered alpha and extremely experimental) Also, Ive been wanting to implement some of the ideas in this paperterm concept: http://www.paperterm.org/notes.html SSH would be useful for a microcontroller without needing a full OS for storing and processing files. Rather, the inputs are relayed like a remote desktop connection. This builds on the Simple Systems concept https://communitywiki.org/wiki/SmolNet which aims to develop a number of small, modular systems than large multilateral systems interacting on multiple levels.

------
Day 7
------

12:00AM I have been curious of shortwave radio, namely skywave propagation: https://en.wikipedia.org/wiki/Skywave

I'm curious if there is way to modulate the low-frequency bands for LoRa-like communication. https://en.wikipedia.org/wiki/LowFER 
"LowFER operation is practiced in the United States and Canada on radio frequencies between 160 kHz and 190 kHz [1] which is sometimes referred to as the 1750-meter band.[2] '
"Many LowFERs are also licensed radio amateurs, although an amateur radio license is not required for LowFER communications in those countries in Region 2, as long as the power is below a nationally prescribed limit, often 1 W.[4][5]"

"Even with such short antennas and low transmit power, LowFER stations have been heard at distances approaching 1,000 miles by listeners using sophisticated receiving setups.[4]"

"MedFER
In the U.S., license-free operation is also allowed on the medium frequency band, also known as the AM Broadcast Band. Similar to LowFER, MedFER is medium-frequency experimental radio. MedFER enthusiasts operate under FCC Part 15 rules using 0.1 W (a tenth of a watt) and a three-meter-long antenna between 510 kHz and 1705 kHz, coinciding with the U.S. AM radio band.[4]"

https://www.qsl.net/dl4yhf/wolf/wolf_info.html

"WOLF
WOLF (Weak-signal Operation on Low Frequency) is a proposed new signal format and protocol designed specifically for the LF bands. It can be used for beacons and for two way communication. Unlike existing formats, which are optimized for a particular S/N (and corresponding speed), WOLF can operate over a wide range of signal levels. For example, a WOLF beacon transmits a 15-character message repeatedly. If the received signal would be adequate for conventional CW, copy will be displayed in 24 seconds. At a level barely enough for 0.4 WPM QRSS, copy will appear within two minutes. Even if the signal is another 10 dB weaker, the message can still be received. It will take from 20 minutes to several hours, depending on the stability of the Tx and Rx. Of course, it is also necessary that the propagation path remain open over the required interval.

I hope that WOLF will permit a QSO to be completed in an hour, if one station receives a signal that is 10 dB weaker than would be needed for QRSS, and the other station's signal is 6 dB below the QRSS threshold. I believe that it is also feasible to "hear" a LOWFER beacon across the Atlantic, during an overnight run (very accurate time and frequency control is required)."

Developing a modem for LowFER for something like the Artemis would be interesting- why use LoRa when there are other unlicensed bands, as long as it is less than 0.1W (for MedFER) and less than 1W for LowFER. While low-frequency doesn't necessarily mean low power- the idea is that it isn't about having a consistent access to a channel, but merely being able to fish out signals and send them out, and the pace or priority being defined later. I plan to find out the power consumption of radiowaves at varying frequencies, to determine if there is anything less power hungry that could be used as a radio for a microcontroller. 

8:59 AM
Part of my detour into shortwave is due to exploring filesystems with a future goal of wireless updates, instead of IC (USB-CH340-based). So, I started to question the entire hardware again, and decided to wander outside the usual suspects (LoRa/LTE, etc). Ham Radio has a long tradition, so I'm sure there's some interesting developments over its 100+ year history. As recently as 2007, "The International Telecommunication Union's 2007 World Radiocommunication Conference (WRC-07) in Geneva agreed a secondary allocation 135.7–137.8 kHz (the so-named 2200 meter band) to the Amateur Service on 9 November 2007, marking the first time since amateur allocations began that there has been an amateur band below the Medium Wave broadcast band. Transmitter power is limited to one watt ERP (meaning an inefficient antenna can be fed a higher power)."

So I'm interested in the intersection between software defined radio, (SDR), and the advances in microcontrollers that allow such low power. Recent microcontroller ports of SDR, such as https://hackaday.com/2020/02/14/rf-shield-turns-arduino-and-pc-into-shortwave-radio/ suggest short wave has a utility on microcontrollers, but using sound cards to convert the signal, is something I need to explore more. Is it the most power efficient method? How does it differ from RF? https://en.wikipedia.org/wiki/Radio-frequency_identification#Frequencies 

LF: 120–150 kHz	Unregulated	10 cm (4 in)	Low	Part 2	Animal identification, factory data collection	US$1 

4 inches might be good enough for an AirDrop replacement ;) 

I have noticed that most of the frequencies begin around 120kHz. I am unsure if this is some kind of physical limitation of signal transfer, or some other impractical reception (such as distance or hardware required- cost, speed, etc). For example, it may not be practical to develop a radio at 12kHz instead of 120khz if it only travels 1cm (using a theoretical "regressive analysis"). Perhaps the frequency is orthogonal to transmit power, and not exactly relevant. Even lower is the Hz and milliHerz (mHz -small m), which may be even more impractical, but I won't make any assumptions. 
