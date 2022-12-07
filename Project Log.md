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

Also, if I were compare the centralized AI narrative to Amazon Prime's The Lord of the Ring's Rings of Power and Lord Sauron, then it would make sense to make in-roads with other sub-cultures such as HAM. Consider me like Elrond, seeking to forge alliances with the King Durin III, the Welshman dwarve with a Scottish accent, and the harfoots with an Irish lilt. https://www.bigissue.com/culture/tv/lord-of-the-rings-the-rings-of-power-star-sophia-nomvete-everyone-could-benefit-from-thinking-like-a-dwarf/

"What’s the thinking behind the accent choices?"

Well, it may not sound obvious, but my impression that it represents a striving towards a United Kingdom- both figurative and literal. Not some fractured Brexit. The term is not widely known, but it is called Bremain: https://en.wiktionary.org/wiki/Bremain Presumably, it represents some kind of symbolic unity against some unknown (or known evil). I prefer to keep a vigilant eye towards any encroaching discord. While ethnic independence can often be source of pride, it can also result in destabilization (e.g Bosnian War, Chechnya, Sudan, etc). My interpretation is just an opinion. I don't think interpretations should always be followed to a logical deduction, since that could lead to varying and conflicting beliefs. 

But, literally shortwave does have a superior technology: "However, shortwave remains important in war zones, such as in the Russo-Ukrainian war, and shortwave broadcasts can be transmitted over thousands of miles from a single transmitter, making it difficult for government authorities to censor them." https://en.wikipedia.org/wiki/Shortwave_radio I reason that DARPA hasn't developed or deployed this technology yet, because it would be seen in Ukraine today if it were ready.

In a way, shortwave is like the <i>mithril</i> in the Dwarvish mine. 

So I'm interested in the intersection between software defined radio, (SDR), and the advances in microcontrollers that allow such low power. Recent microcontroller ports of SDR, such as https://hackaday.com/2020/02/14/rf-shield-turns-arduino-and-pc-into-shortwave-radio/ suggest short wave has a utility on microcontrollers, but using sound cards to convert the signal, is something I need to explore more. Is it the most power efficient method? How does it differ from RF? https://en.wikipedia.org/wiki/Radio-frequency_identification#Frequencies 

LF: 120–150 kHz	Unregulated	10 cm (4 in)	Low	Part 2	Animal identification, factory data collection	US$1 

4 inches might be good enough for an AirDrop replacement ;) 

I have noticed that most of the frequencies begin around 120kHz. I am unsure if this is some kind of physical limitation (i.e. minimum) of signal transfer, or some other impractical reception (such as distance or hardware required- cost, speed, etc). For example, it may not be practical to develop a radio at 12kHz instead of 120khz if it only travels 1cm (using a theoretical "regressive analysis"). Perhaps the frequency is orthogonal to transmit power, and not exactly relevant. Even lower is the Hz and milliHertz (mHz -small m), which may be even more impractical, but I won't make any assumptions. 

6:13 PM

One of the reasons I want to explore LongWave is the presumably lower power. Before I dive more into that, a brief overview of the common wireless power and data transmission efficiencies:

![image](https://user-images.githubusercontent.com/76194453/204935425-f90caecf-5c4b-465c-8659-1e3ac50f23a1.png)
(from above mentioned: https://brandenghena.com/projects/lpwan/ghena19lpwans.pdf) So one of the "conveniences" of LoRa is, that despite it's relatively high power output to apparently lower power shortwave alternatives, there is relatively more infrastructure and equipment ready to to use with microcontrollers. By contrast, LW and SW is relatively a niche market and not as highly commodified as the GSM market. 

Update: I did find some info on the power consumption of very low frequencies (i.e 3- 30kHz): https://en.wikipedia.org/wiki/Very_low_frequency 

https://en.wikipedia.org/wiki/Very_low_frequency#Amateur_use 

"Amateur use
The frequency range below 8.3 kHz is not allocated by the International Telecommunication Union and in some nations may be used license-free. Radio amateurs in some countries have been granted permission (or have assumed permission) to operate at frequencies below 8.3 kHz.[12]

Operations tend to congregate around the frequencies 8.27 kHz, 6.47 kHz, 5.17 kHz, and 2.97 kHz.[13] Transmissions typically last from one hour up to several days and both receiver and transmitter must have their frequency locked to a stable reference such as a GPS disciplined oscillator or a rubidium standard in order to support such long duration coherent detection and decoding."

"Amateur equipment
Radiated power from amateur stations is very small, ranging from 1 μW to 100 μW for fixed base station antennas, and up to 10 mW from kite or balloon antennas. Despite the low power, stable propagation with low attenuation in the earth-ionosphere cavity enable very narrow bandwidths to be used to reach distances up to several thousand kilometers. The modes used are QRSS, MFSK, and coherent BPSK."

Ultra low Frequency, is 300 Hertz to 3kHz: https://en.wikipedia.org/wiki/Ultra_low_frequency

"ELF" or Extremely low frequency, is 3 to 30 Hz: https://en.wikipedia.org/wiki/Extremely_low_frequency 

and under 3Hz is : "Tremendously low frequency" https://en.wikipedia.org/wiki/Radio_spectrum#ITU <3 Hz & 100,000 km"(For reference, the circumference of the earth is 40,000 km)

6:53 PM 

Now, for some quick analysis. Do I think it would be practical for a microcontroller to broadcast an extremely long wave for over an hour, even if it is using microwatts of power? No, because I have solar power in mind. Thus there are so many daylight hours. :) One of the thing I mention in my tri-design approach: https://github.com/EI2030/Low-power-E-Paper-OS/blob/master/wiki/tri-design-approach.md is that the power consumption should not exceed the energy harvesting ability. HOWEVER, one of the interesting utilization aspects of very low, ultra low power base station antennas is that is COULD use less power than the solar panel is able to generate. As a proof of concept, I may only want to transmit 15 characters, or 120 bits. I may not be able to transmit 120 bits per second, but the tri-design approach encourages say...120 bits per hour, if the bill of materials allows for some truly efficient (and borderline comical) telegams- such as the  1 character transmission of "?" and "!" https://www.countrylife.co.uk/country-life/wars-weddings-boiled-eggs-10-memorable-telegrams-ever-sent-174331 

"The shortest telegram in history
This has been attributed to both Victor Hugo and Oscar Wilde. In both cases, the writers are said to have telegrammed their respective publishers to ask about sales of their latest published works.

In both cases, the telegram simply asked ‘?’. The publisher is said to have replied with an equally frugal ‘!’.'

So, just as a proof of concept- I am truly exercising maximum skunkworks here, say a very low, or ultra low frequency could be determined to most efficiently transmit a few characters- under 20 in the most power efficient method- this would factor in the short lived solar irradiance, and the ability for a lithium ion capacitor to store a charge, so that the entire transmission can occur in less than 2.7 hrs, which is said to be the "battery" life of the li-ion capacitor. For example, at night, if one wanted to send an emergency SOS signal, there would be no power to send it, unless the microcontroller/li-ion capacitor charged fully before sunset and it has enough power to send one (or a series of a few) transmissions under 2.7 hrs. Thus, this would be the upper limit, and in practice, a much shorter transmission should be targeted, so that multiple attempts can be used without having to wait til dawn.

As a reference: "If your application draws 30mA from the 3.3V output, then it will run for: 250F(3.78V-2.49V)90%/0.03A= 10750s = 2.7 hrs" https://www.tindie.com/products/jaspersikken/solar-harvesting-into-lithium-ion-capacitor/ If the transmit power is far less than 30mA, then far more than 2.7hrs would be available to transmit an ultra low power, and shortwave frequency. Perhaps 3mA, or 300uA. Something ideally not requiring an hour long transmission, but that setting could even be re-programmed remotely based on realtime weather conditions (although not less than "real-time" it takes to receive an equally long message transmission). If two-way communication is not available, setting transmission times may be better fixed based on climate (predictable, slowly changing averages) or local sensors that can calculate weather /availability without remote updates.

8:44 PM 

Actually, the shortest Morse code is "E", which is 1 character. To differentiate between the a new transmission and the same word, a space is three "dits":

"The dit duration is the basic unit of time measurement in Morse code transmission. The duration of a dah is three times the duration of a dit. Each dit or dah within an encoded character is followed by a period of signal absence, called a space, equal to the dit duration. The letters of a word are separated by a space of duration equal to three dits, and words are separated by a space equal to seven dits.[1] Until 1949, words were separated by a space equal to five dits.[5]

"Morse code is transmitted using just two states (on and off). Historians have called it the first digital code. Morse code may be represented as a binary code, and that is what telegraph operators do when transmitting messages. Working from the above ITU definition and further defining a bit as a dot time, a Morse code sequence may be made from a combination of the following five bit-strings:

short mark, dot or dit (  ▄ ): 1
longer mark, dash or dah (  ▄▄▄ ): 111
intra-character gap (between the dits and dahs within a character): 0
short gap (between letters): 000
medium gap (between words): 0000000"

Thus, Morse code can be encoded in less binary data than 8-bit binary. 

For amateur radio: https://en.wikipedia.org/wiki/Morse_code#Amateur_radio

"Morse code also requires less signal bandwidth than voice communication, typically 100–150 Hz, compared to the roughly 2,400 Hz used by single-sideband voice, although at a slower data rate."

"The narrow signal bandwidth also takes advantage of the natural aural selectivity of the human brain, further enhancing weak signal readability.[citation needed] This efficiency makes CW extremely useful for DX (distance) transmissions, as well as for low-power transmissions (commonly called "QRP operation", from the Q-code for "reduce power")."
https://en.wikipedia.org/wiki/QRP_operation 

"QRPers are known to regularly use less than 5 Watts, sometimes operating with as little as 100 milliwatts or even less. Extremely low power — 1 Watt and below — is often referred to by hobbyists as "QRPP".[4][5][6][10]"

[4] http://www.arrl.org/qrp-more-than-a-state-of-mind
[5] https://books.google.com/books?id=kVpoihOUjNgC 
[6] https://books.google.com/books?id=npwFrgEACAAJ 
[10] https://books.google.com/books?id=hPBINAAACAAJ

----
Day 8
-----

11:25 AM 

"Among the various sections and subsections within Part 15 are a number of interesting provisions. One permits the use of up to 1 watt of power and a 15 meter long antenna between 160 - 190 kilohertz, in the longwave bands, with no license requirement. Another permits similar operation from 510 - 1705 kHz, in the mediumwave band, with 1/10 of a watt and a 3-meter antenna. Yet another allows operation in a 14kHz-wide band centered at 13.56MHz, with a maximum field strength limit that works out to about 4.8mW into a dipole or a quarter-wave vertical over an elevated groundplane.--'

from https://www.lwca.net/sitepage/part15/index-what.htm

0.1 W is 100mW. Thus one could legally transmit MedFER at 1.7Mhz using a 30mA lithium ion capacitor, for 2.7hrs+, assuming it has a 150mW battery output.

How far can 13.46Mhz travel, at under 4.8mW?

I seek to find out.

https://www.rfidcard.com/product-category/rfid-card/hf-13-56mhz/ "The HF band ranges from 3 to 30 MHz, where typically HF RFID systems operate at 13.56 MHz with read ranges between 10 cm to 1 meter. HF RFID systems experience moderate sensitivity to interference. HF RFID applications include ticketing, payment, and data transfer applications.'

As for LF and MF: "Antennas of these lengths are very, very short (electrically) at their respective frequencies. Efficiency is naturally a tiny fraction of a percent. Under average conditions, with an ordinary receiver, it was not expected such signals would reach more than a few tenths of a kilometer.

However, if one is very resourceful at reducing loss in the antenna system and maximizing efficiency in the transmitter, respectable signals can be detected over longer ranges. Use narrowband transmission modes, such as Morse code or more advanced digital methods, and that range can be multiplied further.

Take considerable pains to couple a good antenna to a sensitive, selective receiver in a quiet location (away from manmade static and stray radio signals), and you multiply that range again.

Listen in winter, when static is at a minimum and propagation is better on LF and MF, and you can achieve real DX! Even with the power limits we're talking about, LF and MF experimenters using plain ol' Morse code in past years sometimes spanned 100, 300, and--rarely--800 miles or more. From time to time, full 2-way QSOs take place over these distances. But with developments in very slow CW and other digital modes over recent years, 1000+ mile reception is not uncommon!

While hams often work the world at very low power levels, to be able to work hundreds of miles at these low frequencies, with virtually no transmitting antenna, takes patience, skill, and love of a challenge."

The full 2016 Part 15 Guidelines: https://www.lwca.net/library/reference/FCC/CFR-2016-title47-vol1-part15.pdf

Sources of information on the terms and acronyms of LF radio: http://w1tag.com/files/Acronym.htm 

Some more links:
https://lwca.net/mb/ 

https://lwca.net/sunpage.html 	LWCA Solar Activity Page
http://www.ka7oei.com/
http://www.ka7oei.com/qrss1.html 
http://www.ka7oei.com/ct_lowfer_archive.html
https://lwca.net/sitepage/part15/index.htm 

------
Day 9
------
This wireless detour from the filesystem project has beein leisurely and winded, but productive, and I'm steering it back to its original purpose- a low power, wireless frequency, capable of sustaining a transmitting of low-byte data while being charged by the photovoltaic, or running on li-ion capacitor for a number of hours (presumably the duration between dusk and dawn- or other planned durations). While I'd like to explore more frequencies (TLF, ELF, and some VLF <30 kHz are probably too impractical for the filesystems and cost), I'll start by focusing on some of the hardware for receiving and transmitting between 160 kHz and 190 kHz(LowFER),  MedFER (between 510 kHz and 1705 kHz), and HiFer (13.56 MHz):

"Vendors of kits or equipment (especially transmitters) for these bands are pretty much non-existent these days. Ramsey Electronics once had kits suitable for AM (MedFER) and FM Part 15-type transmitters, but left the kit business entirely in 2016. North Country Radio used to sell at least one kit suitable as a foundation for either a MedFER  or LowFER transmitter, but the AM88 is now obsolete and the former LF-90 LowFER transmitter is no longer mentioned on their website at all. So, of necessity, the hobby requires a little bit of electronics experience if you wish to transmit. The gear need not be fancy, and you can find examples in the Library section of this site. As for receiving:

"LF Engineering manufactures active longwave receiving antennas, upconverters to shift the LF spectrum into range of a good shortwave receiver, and other useful hardware. You can't work 'em (or even just log other Part 15 stations) if you can't hear 'em." (From the above lwca part 15 index link)

This is one such product: 
https://www.lfengineering.com/products.cfm

One such receiving antenna: "	
L-111S - LF/VLF Converter/Antenna System
Price: $269.00

IF Output Frequency	4 to 4.5 MHz
Frequency Response	10 kHz to 530 kHz +/-5 dB
 
The L-111 System provides full coverage of the LF spectrum from less than 10 kHz to 530 kHz. The L-111 combines the proven L-400B active antenna with a sensitive LF to HF converter. The externally mounted LF converter contains a low impedance wide dynamic range balanced mixer, with RF, IF and local oscillator filtering. The converter's high L.O. rejection greatly improves reception below 10 kHz and its sharp roll-off filter characteristics eliminate BC intermodulation. Receiver tuning is between 4.0 MHz and 4.5 MHz."

So it could pick up a LoWFER signal between 160-190 kHz and then upconvert it to a range that a more conventional shortwave radio can pick up in the low Mhz range! I'm sure there is some other equipment needed.

QRS
Some of the software/hardware combos make it practical to allow the PC to run for an hour or two to do the receiving and transmitting of very slow signals that would require much human patience to decode, if even possible (with very faint frequencies): "In order to beat the high QRM and QRN levels on the 136kHz ham band very slow CW is used (speeds going from 0.4 WPM even down to 0.01 WPM). QRS allows you to key your TX at these extreme slow speeds using the serial or parallel port of your PC."

I am curious if this serial converter could be useful for a microcontroller receiving inputs from a 232 port: https://www.adafruit.com/product/2264 Some type of keyboard based microcontroller could allow one to type and display the keys being sent, similar to some of the LoRa messengers and Keyboard Featherwing, except on the shortwave band:
https://shop.pimoroni.com/products/keyboard-featherwing-qwerty-keyboard-2-6-lcd

https://hackaday.com/2022/05/25/long-distance-text-communication-with-lora/

I suppose you could call it a long wave messenger. A little background on technological convergence: https://en.wikipedia.org/wiki/Technological_convergence 

"Technological convergence is the tendency for technologies that were originally unrelated to become more closely integrated and even unified as they develop and advance. For example, watches, telephones, television, computers, and social media platforms began as separate and mostly unrelated technologies, but have converged in many ways into an interrelated telecommunication, media, and technology industry."

A portable, solar powered, longwave (or shortwave) messenger would represent a convergence of unrelated technologies, much like how the cell phone converged watches, telephony, rolodexes, composition of letters, and even in-person meetings. While the internet allows efficient detachment from human interaction to replace conventional activities, it also allows increased human interaction in distilled text. That is, an IRC chatroom allows more viewpoints to be shared, even moderated, for more balanced viewpoints (assuming the room isn't overrun by bots and the like), with one of the largest benefits is the (more or less) being the ability to communicate with anyone over the world, consiering an international phone call for much of the 2nd half of the 20th century was one of the few ways to talk/chat in real time (until the internet became widespread). Thus the disruptive innovation of the telegraph, then the undersea phone lines, then the internet, progressively decreased the cost to communicate over longer distances. Since many of technologies needed to make that happen have been built (albeit 5G is more of an optimization, rather than some revolutionary transformation), there is much more time to converge and optimize autarkic low data devices by mixing and matching "unrelated" technologies (which are technically a convergence of previous generations' technologies).

To make an analogy to pharmacology "Drug design, often referred to as rational drug design or simply rational design, is the inventive process of finding new medications based on the knowledge of a biological target.[1]" https://en.wikipedia.org/wiki/Drug_design#Rational_drug_discovery

"The phrase "drug design" is to some extent a misnomer. A more accurate term is ligand design (i.e., design of a molecule that will bind tightly to its target).[6] Although design techniques for prediction of binding affinity are reasonably successful, there are many other properties, such as bioavailability, metabolic half-life, side effects, etc., that first must be optimized before a ligand can become a safe and efficacious drug."

"In contrast to traditional methods of drug discovery (known as forward pharmacology), which rely on trial-and-error testing of chemical substances on cultured cells or animals, and matching the apparent effects to treatments, rational drug design (also called reverse pharmacology) begins with a hypothesis that modulation of a specific biological target may have therapeutic value."

"Molecular modelling encompasses all methods, theoretical and computational, used to model or mimic the behaviour of molecules.[1] The methods are used in the fields of computational chemistry, drug design, computational biology and materials science to study molecular systems ranging from small chemical systems to large biological molecules and material assemblies."

In solar powered mobile devices, the "ligand" in this case is the TDP. Designing a portable wireless communication device that is solar powered requires centering development around some efficiacious advantage that would allow more users to adopt technologies they would otherwise not want or use. For example, many Android phones
still ship with FM radios, along with GPS compasses, and a digital watch. Before navigations systems were available, few, if any people would walk around with portable radios until the Sony Walkman in the 1970s. So, for the most part, a pocketwatch was the most electronic/mechanical device someone would wear or carry before the 1970s. Today, the average consumer is going to seek features such as 120Hz or an OLED foldable display, and not mind if it has a portable radio or not. Of the huundreds or thousands of hardware technologies (let alone millions of software technologies) in a single cell phone today, the one feature they are all missing is that it can't work without a battery, while  state of the art technologies today already can make that happen with microcontrollers with autarkic sensing abilities, aided with solar and other scavenging tech like https://e-peas.com/

So the feature here, is using a microarray- a combination of known electronic hardware libraries (all of the shortwave bands), and using rational (but also random, [highthroughput ](https://en.wikipedia.org/wiki/High-throughput_screening)

"High throughput screening" does not imply that it is a random selection from a molecular library- it could be a carefully selected array of compounds- using both rational analyis (human) and computer aided analysis-statistic or algorithmic, etc, to determine the most efficacious design.


In this analogy, the "ligand" is the frequency- whether it is LoFER or MEDFER, and the "receptor" is the microcontroller, whether can transmit data fast enough for human consumption, using a power consumption that also meets the average photovoltaic harvesting ability in a chosen location for the autarkic device (whether it is stationary, like on a telphone pole or a mountain top, etc) or portable for human mobility use.

Since static interference increases the lower the spectrum:

"Consider how static levels increase as you go down the spectrum. By the time you get below 500 kHz, most receivers are deliberately far less sensitive than they are in the shortwave bands. The assumption is that, at LF, you won't be wanting to hear anything but the strongest signals over the noise anyway."

""QRP enthusiasts may use special modes that employ technology and software designed to enhance reception of the relatively weak transmitted signals resulting from low power levels.[11]

QRSS: Very slow speed Morse code

QRSS uses very slow speed CW (Morse code) to compensate for the decreased signal-to-noise ratio involved in QRP operation.[11][b] QRSS enthusiasts may record a transmission for later analysis, sometimes decoding "by ear" while playing it back at much faster speeds, or decoding "by eye" on the waterfall display of a spectrum analyzer.[12][13]" https://en.wikipedia.org/wiki/QRP_operation#QRSS"

Transplanting the microarray idea to radio frequencies is like testing which frequencies have the best signal to noise ratio- one that software can solve with Fast Fourier Transform http://www.ka7oei.com/qrss1.html) while balancing the tradeoffs of lower bandwidth and transmit power- that is, if a human is only going to check their email once every ten minutes on a smart watch, while on a nature walk, then the wearable only needs to transfer the data indicating that there is a new email, rather than downloading the entire contents. Not only that, but EMF interference, magnetic immunity are all risk factors in converging disparate electronics like HAM radio receiving antennas with low nanometer <sub 20nm FinFET) microcontrollers. Thus there are many unknowns when physically designing a single board computer with lots of sensitive radios and displays so the idea here is to test many different frequencies with many different microcontrollers. One may not need radiation hardened, 180nm chips for something like a walk in the park, but more like "if i can get a signal", then type "Hi Mom"; if not, {I'll say hello when I get home/get a signal}. Nonetheless, it shouldn't stop one from trying!  

For example, this wonderful page on GPS placement actually examines why and where GPS antennas are installed on phones, to maximize signal (or poorly selected locations): https://www.antenna-theory.com/design/gps.php

The application of a medication sometimes uses a slow release capsule "Delayed-release (DR) medications are medications that are designed to release the active ingredient(s) later after taking it* Obviously this has a vital purpose, but consider applying this to technology, rather than use a "Just-in-time" (JIT) or even overly cached "Tsundoku," approach. It is the Japanese word for the New Books That Pile Up on Our Shelves: https://www.openculture.com/2018/07/tsundoku.html

Today's phone have over 128GB of internal storage/eMMC, and up to 2TB of microSD storage. A lot of times it is convenient, right? But that amount of storage also requires a lot of power to access, even if it is relatively low compared to RAM and 5G antennas. Many in a developed nation who buy a Raspberry Pi aren't buying it for their first computer. They are probably using it as a test board, or a server, or a video game. Usually that is the case- a wealthy person who owns an electric car, unless they live in a city, probably owns another car that uses an internal combusion engine, because electric cars are status symbols in a way (maybe not in Norway). Ideally, the cost of electric batteries will be lowered by way of replacement with a "greener" energy storage medium, so that many more people one day consider electric cars like ICE cars- in fact, no distinction should be made regarding whether something is "poor" or not. The manufacturability of microcontrollers is possible to exceed that of global human population. Likewise, the raw materials required to manufacture a secondary, solar powered phone/sms device, especially one that could last longer than a planned obsolescence of a product would be far more justified than one part of a short product cycle (with far heavier lithium packs).

Thus having a 2nd or 3rd (or 10 PCs), unless one is a computer researcher, is usually a clutter. And likewise, having a high speed internet connection on a mobile device is often unnecessary for leisurely strolls to a nearby park. One might just want to have a phone for calling or texting, not to immerse oneself in a super gamified social network while sitting on a park bench or taking long walks on the beach. Thus, having a wireless technology that meets the data requirements of the application, but does not exceed it's use case, can benefit from other frequencies that transmit data further, and possibly at a lower uW/Byte than the higher frequencies. Thus, "delayed release" is like having a pre-defined schedule- screen time limited with all or most notifications turned off, and to allow just enough words per minute that the activity requires. For example a reading exercise might stream a text from a home based radio transmitter 1000 feet away, asking, "what's for dinner?" this might be an exercise to encourage returning home on a walk not to exceed a mile, and the the phone, having less transmit power, may be prompted to type a single digit to choose from a list- "1" for  pasta" "2" for "meat and potatoes" or 3. "rice and beans." These kinds of communication devices could be inexpensive and less noisy than a 2 way radio, not to mention solar powered...(ok, i mentioned it again). Sending enough "reading material" for a short walk, the "delayed release" concept can be distilled to having just enough data to not cause information overload ("overdose" without DR) on what is supposed to be a carefree nature walk.

LowFER has been compared to birdwatching: http://www.ka7oei.com/ct_lowfer_archive.html

"The big question:  Why?

Why do all of this?  Former (?) LowFER Don Pomplun (K2BIO) put it well:  "A friend asks why I would be interested in listening to weak stations that in fact don't even have anything to say.  I've found that LowFERing and ham radio can be likened to bird watching:  That answer seems to be more acceptable, even if no more explainable!

So, it makes sense that a portable shortwave transmitter be used for low-tech (like outdoorsy activities) activities (though using newly converged old concepts on more power-efficient SoC platforms) 

Microcontrollers historically and continue to be lower cost than general purpose CPUS, and the speed they run at today in the hundreds of megahertz, is sufficient to decode longwave radio that transmits at less than 100mW, and theoretically could converge with a number of other state of the art technologies, solar panels, capacitors, memory in pixel displays, and QRSS https://www.qsl.net/m0ayf/What-is-QRSS.html to almost run autonomously not just with rooftop solar, but handheld solar panels. 

Thus, the convergence is the minimum 8-byte text protocol using modern 32-bit microcontrollers, which may have more access to I/O than an 8-bit device, thus a 5-bit Morse may be impractical if it does not save any data on architecture that cannot pack less data in 5 bit if 8 bit is required (I don't actually know the answer to that), but presumably a 100 bit per second radio frequency would not have much efficiency loss. According to the chart from Day 7, LoRaWAN at 143dB transmits 200 Bytes per 24 hrs at an average of 1.1uW. That is very low, and a small portable solar panel should easily be able to handle that. The question then, is what benefits would shortwave and longwave have over LoRA? Longer distance, perhaps at a higher transmit power, but not impossible to do under the Part 15 regulation of 0.1W-1W, even with portable equipment.

While I will revisit LoRA, I found this interesting article on the average distance of AM Radio stations: https://www.fcc.gov/media/radio/am-stations-at-night "Useful daytime AM service is generally limited to a radius of no more than about 100 miles (162 km), even for the most powerful stations. I was also unaware of this other LoRa band: https://en.wikipedia.org/wiki/Wize_technology

However, during nighttime hours the AM signals can travel over hundreds of miles by reflection from the ionosphere, a phenomenon called "skywave" propagation."

1:14PM https://en.wikipedia.org/wiki/Amateur_radio#Text_and_data While there are many real-time, digital teletext methods of transmitting and converting radio waves into digital, some require the use of GPS, such as FT8. While some of these technologies may exploit available technologies at hand, the goal of this solar powered texting or SIP device is to use as few modules as possible (GPS and additional microcontrollers would result in additional power consumption, usually), so the balance here is trying to find one microcontroller than could process all radio input, i/o display and keyboard, as well as radio output, and all without a battery.

3:44 PM

When I was young, I checked out the Carl Sagan-based movie Contact from the local library. While I never got into ham, I've always understood this scene to represent greater space/universe exploration: https://www.youtube.com/watch?v=Y2_KMVBmEgc

-------
Day 10
-------

10:00AM

I found some interesting ham-technology, utilizing what's called a TNC: https://en.wikipedia.org/wiki/Terminal_node_controller. A great article posted in the IEEE last December: https://spectrum.ieee.org/ham-radio-text-hacking points out that there is a texting service, but someone from a younger generation, not unlike me, decided software and portable hardware might be an additional use-case of ham:

"However, I found that just talking over ham radio was boring for me. I started thinking about an old police scanner my dad owned and how we would sometimes hear odd sounds that sort of sounded like a dial-up modem. And that is when the lightbulb for HamMessenger turned on. What if I could find an easy way to communicate digitally with my handheld radio?"


"APRS supports sending text messages, and if you're in range of an Internet-connected gateway node you can even exchange SMS texts with cellphones and send one-line emails. Sending texts traditionally meant using a PC hooked up to a so-called terminal node controller (TNC) packet radio modem, which is in turn connected to a radio (signals are transmitted as audio tones, just like old dial-up modems). More recently, TNC modems that interface with smartphones have been created. And these are awesome projects! But at its core, HamMessenger was created in the shadow of my simple childhood experiences. I wanted a portable device I could connect to my handheld radio that was completely self-contained, with a keyboard, screen, and GPS receiver all built in."

It sounds like an ambitious project and I think it's quite along the lines of what I had in mind, except I do not think the GPS aspect, however integral, would be possible to run on a battery-free microcontroller (in a portable medium), at least with today's tech. That said, I will stay up to date with it and reach out to them to see if there are any MedFER or LowFER transmission techniques.- maybe even a LowFER to HF upconverter that could be paired with an Artemis or Ambiq Apollo3.

https://smsgte.org/ A very interesting new tech (if 2014 is considered new): "This gateway, known as SMSGTE (pronounced sms geit) was launched in 2014 as a means of reaching loved ones when out in areas uncovered by cellular services. Since then, the gateway has grown to serve 6000 users, with over 1000 users added in 2020."

https://github.com/markqvist/MicroAPRS upgraded by https://github.com/markqvist/OpenModem -  110 Euro out of stock. "Open Modem Firmware is an open source firmware implementation of a AFSK modem supporting 300, 1200 and 2400 baud operation, suitable for communication over a wide variety of analogue mediums, both radio and wired."

A modem developer was using ham in Denmark, where encryption is allowed: http://unsigned.io/articles/2018_06_30_15-kilometre-ssh-link-with-rnode.html "This is not the case where I live, so even heavily encrypted things like SSH are perfectly fine in ham radio here."

Well, for what I'm researching, encryption is not going to be possible at the lowest power/data unit - since the signal will be as low as needed: 
https://sookocheff.com/post/networking/wireless-networks-and-shannons-law/

![image](https://user-images.githubusercontent.com/76194453/205451206-74910fe1-0266-4f07-af0f-a7222b72877c.png)

where:

C is the capacity of the channel, measured in bits per second

W is the available bandwidth, measured in hertz

S is the power of the received signal, measured in watts

N is the power of the received noise, measured in watts

Shannon’s work showed that the values of SS, NN, and WW set a limit upon the transmission rate — the two fundamental constraints on achievable data rates are the amount of available bandwidth and the ratio of signal to noise between the receiver and the sender.

From this previously linked page: "Becoming Narrow-Minded:

"For a given modulation type (in this case, on-off keyed CW) the lower the "data rate", the narrower your transmitted signal, the narrower the required receive bandwidth, and the lower the lower the transmitted power required to maintain that "threshold of copiability."  Communications theory (Shannon's Law) states that if you were willing to transmit your data infinitely slowly you could communicate with infinitely narrow detection bandwidth and infinitely low (not zero) power.  It should go without saying that there are practical limits to how slow you would go to convey useful information in a reasonable amount of time." http://www.ka7oei.com/qrss1.html

In this "exploratory stage", I am not selecting a frequency or filter before I can determine what is the minimum CW signal needed to allow it to be received, presuming a receiver "elsewhere" is tuned exactly to the same frequency. That said, if there were two developers working on this, or the initial developer drove to another location and set the frequency to the same as the transmitting radio (at the most narrow one possible allowed by Shannon's law), then the power needed would approach zero. In practice, one can decide whether they will need to transmit a single character or three. In any case, the binary- dit and dah, may require more than sending just an "E."

But as this concept is established, I seek to apply this to batteryless microcontrollers, because speed of transmission is not the top priority at this moment. Proof of concept is- that is, sending a single CW signal: in this case- let's say 90 seconds:

"QRSS generally means that the CW sending speed is below 2-3 WPM - usually much slower than that.  Let's take as a rather extreme example, the VA3LK beacon on 137.79 Hz.  This experimental beacon has operated at a "dit" rate of one dit every ninety seconds - that's about .0133 words-per-minute, or about 0.8 words-per-hour.  This also implies that the detection bandwidth for such a signal (see the equations below) should be at least 0.033 Hz - that's 33 Millihertz (mHz - notice the small "m"!)  Going much much narrower than this and the "dits" will start to run together and sacrifice "intelligibility."

At the border between intelligibility and unintelligible signals resulting between propagational phase shifts:

"There is another factor that should be considered:  Propagational phase shifts:
 
"Seeing" the dits and dahs
"Reading" the dits and dahs from a waterfall display takes a bit of getting used to, but it is really quite effective in digging the signals out of the "noise."  Even the slightest trace of signal on the display can be perceived by the eyes:  The brain is very good at picking bits of order out of visual chaos... 

One suggestion that I would make:  When you have, for certain, determined the length of the dits and dahs, it helps to mark their "length" on a piece of paper.  When QSB or QRM occurs, holding that piece of paper up the the screen can help make the decision whether or not what is on the screen is "too long for a dit" or "too short for a dah."  This method depends on the "scroll" speed of the waterfall display being constant - something that may not be true - especially on computers slower than a 200 MHz pentium.

In effect, changing the phase of a signal on a particular frequency is the same thing as changing its frequency during the change.  Let's suppose that we have a 1 Hz tone.  If we were to retard the phase of it by 360 degrees every second, then we are "eating" one cycle every second, resulting in a 999 Hz tone.

Propagation is a tricky thing:  A very distant signal will likely arrive at the receive point via a skywave.  Over that distance the effective path length could change slightly.  At our example frequency of 137.79, the wavelength is approximately 2 kilometers:  The total distance the signal travels to get to the receive site 2000+ km away could easily change by 1 km in the course of a minute or so, resulting in a 180 degree phase change.  Since a phase change amounts to a frequency change, that signal may have actually moved while you were trying to "copy" that dit.  It is for this reason that one may want to avoid running narrower filters than you absolutely have to.  Fortunately, LF propagation is quite stable and these sorts of effects are much less prevalent than on HF."

So, running at a frequency that causes or is susceptible to phase shifts should be avoided, since it could be impossible to discern signal from noise without understanding whether a LF propagation is stable or now.

Applying that to a portable texting ham- on an unlicensed band such as 1.7Mhz, it would be easy to see how other signals could get mixed up and not easy to discern who is sending them. Thus, in a given region, it may be useful to assign call signs that use equipment that have a defined range (which might not preclude skip propagation), but could be sufficient to discern (with predefined frequencies such as on an email mailing list) which "E"s are being sent and which dit-dahs are being sent by whom. This thus would be an informal distinction, provided all ham users play by the rules. More sophisticated callsigns would be possible with higher character counts, which could of course be used for the standard call signs.

------
Day 11:
------
9:59 AM 
I started this project just over 2 weeks ago, with a few days without posting for holiday. Whenever I try to work on a project, and I have the time, I tend to enjoy immersing myself in the subject, spending long blocks of a day without interruption of a train of thought. The "practice" is called: https://en.wikipedia.org/wiki/Flow_(psychology) A good balanced is always important.

Today, I'll focus initially on radio congestion- and the history of it. I will start around the Radio Act of 1912, but I may find other regulations in other countries that also may be intresting/relevant (probably). Basically the reason for this inquiry is, how was GSM, unlike receiving radios (excluding ham) for now), determined to have enough frequencies for million of cell phone users? Surely there are a limited number of frequencies for a given band, and without assigning or sharing the band some way, there would be a lot of interference, much like WiFi networks in a congested building can too. Of course this also can occur for ham and other bands, such as https://en.wikipedia.org/wiki/Citizens_band_radio: 

"In many countries, CB operation does not require a license, and (unlike amateur radio) it may be used for business or personal communications. Like many other land mobile radio services, multiple radios in a local area share a single frequency channel, but only one can transmit at a time. The radio is normally in receive mode to receive transmissions of other radios on the channel; when users want to talk they press a "push to talk" button on their radio, which turns on their transmitter. Users on a channel must take turns talking. Transmitter power is limited to 4 watts in the US and the EU. CB radios have a range of about 3 miles (4.8 km) to 20 miles (32 km) depending on terrain, for line of sight communication; however, various radio propagation conditions may intermittently allow communication over much greater distances."

https://en.wikipedia.org/wiki/Radio_Act_of_1912

There is a lot of interesting history, too much to cover here, but some of the first transatlantic shortwave- from England to NewFoundland are fascinating: 
https://en.wikipedia.org/wiki/Poldhu

"Fleming estimated the transmitter's radiated power was around 10–12 kW.[10] The frequency used is not known precisely, as Marconi did not measure wavelength or frequency, but it was between 166 and 984 kHz, probably around 500 kHz.[6] After the experiment the original mast layout was not rebuilt, it was replaced with a four mast design, 215 feet (66 m) high and forming a 200-foot (61 m) square.


Area of the station in the year 2007, antennas operated by the Poldhu Amateur Radio Club
Marconi later used the site for his shortwave experiments, with transmissions by Charles Samuel Franklin to Marconi on the yacht "Elettra". in the Cape Verde Islands in 1923 and in Beirut in 1924. The groundbreaking results of these experiments took the world by surprise and quickly resulted in his development of the Beam Wireless Service for the British General Post Office. The service opened from the Bodmin Beam Station to Canada on 25 October 1926, from the "Tetney Beam Station". to Australia on 8 April 1927, from the "Bodmin Beam Station". to South Africa on 5 July 1927, to India on 6 September 1927 and shortly afterwards to Argentina, Brazil and the United States."

https://en.wikipedia.org/wiki/Wireless_telegraphy " Beginning about 1908, powerful transoceanic radiotelegraphy stations transmitted commercial telegram traffic between countries at rates up to 200 words per minute."

"Wireless telegraphy or radiotelegraphy, commonly called CW (continuous wave), ICW (interrupted continuous wave) transmission, or on-off keying, and designated by the International Telecommunication Union as emission type A1A or A2A, is a radio communication method. It was transmitted by several different modulation methods during its history. The primitive spark-gap transmitters used until 1920 transmitted damped waves, which had very wide bandwidth and tended to interfere with other transmissions. This type of emission was banned by 1934, except for some legacy use on ships.[5][6][7] The vacuum tube (valve) transmitters which came into use after 1920 transmitted code by pulses of unmodulated sinusoidal carrier wave called continuous wave (CW), which is still used today. To receive CW transmissions, the receiver requires a circuit called a beat frequency oscillator (BFO).[8][9] The third type of modulation, frequency-shift keying (FSK) was used mainly by radioteletype networks (RTTY). Morse code radiotelegraphy was gradually replaced by radioteletype in most high volume applications by World War II."

" In tests across the Bristol Channel in 1892, Preece was able to telegraph across gaps of about 5 kilometres (3.1 miles). However, his induction system required extensive lengths of antenna wires, many kilometers long, at both the sending and receiving ends. The length of those sending and receiving wires needed to be about the same length as the width of the water or land to be spanned. For example, for Preece's station to span the English Channel from Dover, England, to the coast of France would require sending and receiving wires of about 30 miles (48 kilometres) along the two coasts. These facts made the system impractical on ships, boats, and ordinary islands, which are much smaller than Great Britain or Greenland. Also, the relatively short distances that a practical Preece system could span meant that it had few advantages over underwater telegraph cables."

https://en.wikipedia.org/wiki/Radioteletype#Technical_specification 

"The original (or "Baudot") radioteletype system is based almost invariably on the Baudot code or ITA-2 5 bit alphabet. The link is based on character asynchronous transmission with 1 start bit and 1, 1.5 or 2 stop bits. Transmitter modulation is normally FSK (F1B). Occasionally, an AFSK signal modulating an RF carrier (A2B, F2B) is used on VHF or UHF frequencies. Standard transmission speeds are 45.45, 50, 75, 100, 150 and 300 baud.

Common carrier shifts are 85 Hz (used on LF and VLF frequencies), 170 Hz, 425 Hz, 450 Hz and 850 Hz, although some stations use non-standard shifts. There are variations of the standard Baudot alphabet to cover languages written in Cyrillic, Arabic, Greek etc., using special techniques.[15][16]"

"Common carrier shifts are 85 Hz (used on LF and VLF frequencies), 170 Hz, 425 Hz, 450 Hz and 850 Hz, although some stations use non-standard shifts."

"Some combinations of speed and shift are standardized for specific services using the original radioteletype system:

Amateur radio transmissions are almost always 45.45 baud – 170 Hz, although 75 baud activity is being promoted by BARTG in the form of 4-hour contests.[17]
Radio amateurs have experimented with ITA-5 (7-bit ASCII) alphabet transmissions at 110 baud – 170 Hz."

RTTY transmissions on LF and VLF frequencies use a narrow shift of 85 Hz, due to the limited bandwidth of the antennas.

https://en.wikipedia.org/wiki/Radioteletype#Comparison_with_other_modes 

"RTTY has a typical baud rate for Amateur operation of 45.45 baud (approximately 60 words per minute). It remains popular as a "keyboard to keyboard" mode in Amateur Radio.[37] RTTY has declined in commercial popularity as faster, more reliable alternative data modes have become available, using satellite or other connections.

For its transmission speed, RTTY has low spectral efficiency. The typical RTTY signal with 170 Hz shift at 45.45 baud requires around 250 Hz receiver bandwidth, more than double that required by PSK31. In theory, at this baud rate, the shift size can be decreased to 22.725 Hz, reducing the overall band footprint substantially. Because RTTY, using either AFSK or FSK modulation, produces a waveform with constant power, a transmitter does not need to use a linear amplifier, which is required for many digital transmission modes. A more efficient Class C amplifier may be used.

RTTY, using either AFSK or FSK modulation, is moderately resistant to vagaries of HF propagation and interference, however modern digital modes, such as MFSK, use Forward Error Correction to provide much better data reliability."

https://en.wikipedia.org/wiki/Baudot_code
"The Baudot code [boˈdo] is an early character encoding for telegraphy invented by Émile Baudot in the 1870s.[1] It was the predecessor to the International Telegraph Alphabet No. 2 (ITA2), the most common teleprinter code in use until the advent of ASCII. Each character in the alphabet is represented by a series of five bits, sent over a communication channel such as a telegraph wire or a radio signal by asynchronous serial communication. The symbol rate measurement is known as baud, and is derived from the same name."

"ITA2 is still used in telecommunications devices for the deaf (TDD), Telex, and some amateur radio applications, such as radioteletype ("RTTY"). ITA2 is also used in Enhanced Broadcast Solution, an early 21st-century financial protocol specified by Deutsche Börse, to reduce the character encoding footprint.[19]"

https://en.wikipedia.org/wiki/Telex

https://en.wikipedia.org/wiki/List_of_VLF-transmitters  <100 kHz 

Some interesting Hackaday articles:

https://hackaday.com/2015/09/27/demonstrating-baudot-code/ 

https://hackaday.com/2015/10/20/the-case-for-arduino-in-real-engineering/


https://en.wikipedia.org/wiki/Morse_code
"While voice and data transmissions are limited to specific amateur radio bands under U.S. rules, Morse code is permitted on all amateur bands — LF, MF, HF, VHF, and UHF. In some countries, certain portions of the amateur radio bands are reserved for transmission of Morse code signals only.

Because Morse code transmissions employ an on-off keyed radio signal, it requires less complex transmission equipment than other forms of radio communication. Morse code also requires less signal bandwidth than voice communication, typically 100–150 Hz, compared to the roughly 2,400 Hz used by single-sideband voice, although at a slower data rate." (I actually quoted this previously), but will leave it in.

An interesting movie: https://youtu.be/r4d27wqQX6k?t=3796 blind piano tuner who's first language is Morse, based on a book by Mai Jia: https://en.wikipedia.org/wiki/The_Silent_War_(2012_film) 

----
Day 12
----

Today I hope to cover more network congestion, which I intended to yesterday. Thinking about one of the quotes from Day 10 seem to identify the minimum bandwidth for any Morse dit- 33 millihertz: 

"QRSS generally means that the CW sending speed is below 2-3 WPM - usually much slower than that. Let's take as a rather extreme example, the VA3LK beacon on 137.79 Hz. This experimental beacon has operated at a "dit" rate of one dit every ninety seconds - that's about .0133 words-per-minute, or about 0.8 words-per-hour. This also implies that the detection bandwidth for such a signal (see the equations below) should be at least 0.033 Hz - that's 33 Millihertz (mHz - notice the small "m"!) Going much much narrower than this and the "dits" will start to run together and sacrifice "intelligibility.""

Having several frequencies spaced 33 millhertz apart probably doesn't sound practical, but it could just be that technology evolved faster than the time spend on optimizing and building transmitting and receiving tools at this frequency. 137Hz, quite an uncommon frequency, falls in the SLF designation: https://en.wikipedia.org/wiki/Super_low_frequency 

"Super low frequency (SLF) is the ITU designation for electromagnetic waves (radio waves) in the frequency range between 30 hertz and 300 hertz. They have corresponding wavelengths of 10,000 to 1,000 kilometers. This frequency range includes the frequencies of AC power grids (50 hertz and 60 hertz). Another conflicting designation which includes this frequency range is Extremely Low Frequency (ELF), which in some contexts refers to all frequencies up to 300 hertz.

Because of the extreme difficulty of building transmitters that can generate such long waves, frequencies in this range have been used in very few artificial communication systems. However, SLF waves can penetrate seawater to a depth of hundreds of meters."

Edit: the quote, while verbatim, appears to be referring to 137kHz, not 137Hz. Thus there is a typo. This was after googling VA3LK:

http://qsl.net/ve7sl/136.html

"QRSS DX

Activity from my station has so far been centered upon receiving. Almost all DX work on LF utilizes the slow speed CW or QRSS mode. The most popular software for decoding QRSS signals is ARGO by I2PHD and IK2CZZ. It is freely available at various web sites for downloading (see LINKS section). ARGO is a very intuative user-friendly program and works extremely well. Accordingly, my first attempts at low frequency QRSS work were directed towards listening for signals from Larry Kayser (SK), VA3LK. Larry was on a nightly transmitting schedule in an attempt to see if his signal could be heard in New Zealand.
Here is a screen capture of Larry's 2200m QRSS signal as received on 06/23/01 at 0944 UTC.

VA3LK ON QRSS
QRSS signals are usually too weak to be actually heard by ear. ARGO allows signals buried in the noise to be 'seen' rather than 'heard'. The screen capture above clearly shows the sequence
"K   V A 3 L K". The signal abruptly faded out at Larry's sunrise in the middle of the next "V".

PUSHING THE BOUNDARIES... Seven days later, my overnight screen captures showed the weak signals of amateur station ZL6QH, transmitting from Quartz Hill, New Zealand on 184.4kHz. This was the first transpacific reception of LF amateur signals from New Zealand to North America, a distance of 11,715km.

ZL6QH QRSS SIGNAL
ZL6QH was transmitting QRSS in the DFCW mode which meant the 'dots' were shifted in frequency slightly from the dashes. Unfortunately my receiver calibration was slightly off and I had only captured the 'dots' and missed the dashes just a few hertz lower. Subsequent transmitting tests were eagerly monitored by numerous other stations in North America and quickly confirmed that long-distance propagation was possible, even at amateur power levels. The ZL6QH signal has now been heard as far back as VE1 land!

My next attempt at seeing the ZL6QH signal was in September of 2001. This time I made sure my receiver calibration was set correctly. Note the abrupt fade-out at my local sunrise. ZL6QH was sending the letter 'Q', with the lower signal representing dashes, the higher one dots. Note that the two dashes are run together, appearing as one long dash in order to conserve time.

ZL6QH QRSS SIGNAL
The best reception of ZL6QH on 137kHz was obtained in December of 2002. Almost four hours of continuous "Q's" were noted until the sunrise fade-out shortly after this screen shot. Note from the ARGO calibration scale that the two signals are only .4 Hz apart."

I found quite a few interesting things:

"LF history was made in the early hours of September 28th, 2010 when Scott, VE7TIL and Kuni, JA7NI completed the first Asian to North American QSO on the 2200m band! Spanning a distance of almost 7200km, the groundbreaking trans-Pacific QSO was the second longest on record.""

http://www.weaksignals.com/  ARM-based SDR:https://www.i2phd.org/armradio/index.html this SDR software uses a 180 Mhz micocontroller, an ARM Cortex M4:
https://www.st.com/en/microcontrollers-microprocessors/stm32f429-439.html  180 MHz, 256KB RAM.
On personal correspondence, I was told that any ports will require enough processing power. Thus it would need to run at at least 180Mhz. Perhaps the Ambiq Micro Apollo4 fits that, when running at 192Mhz. 

2019 Review of SDR software: https://www.lloydm.net/Demos/LWSDR.html

https://www.i2phd.org/code/ARM_Radio.pdf 
https://www.i2phd.org/code/ARM_Radio.zip 
Software for SDR, such as Argo and Spectran 
http://www.qsl.net/on7yd/136narro.htm#QRSS
http://www.472khz.org/pages/technical-topics/weak-signal-modes.php
https://www.qsl.net/on7yd/136narro_old.htm
http://www.mgef.org/zms_241_vucc.htm There's even 75 Ghz  mmWave, site currently down
https://wireless.org.uk/newspic52.htm


 
RFID: While RFID doesn't have the same range, I'm curious if there'd be a benefit to hybridizing the approach for a microcontroller- i.e a phone might not work well indoors for a cell tower, but could use a repeater +/- router, hybridizing RFID and LoRa or other band: 

https://electronics.stackexchange.com/questions/109079/rfid-data-transfer-rates
"LF - 125-134 kHz

"I know that in LF at least, the data rate is normally a simple divider from the carrier frequency. A 128 kHz carrier might be divided by a factor of 32 or 16 to create a data rate 4 or 8 kbps, for example"
HF - 13.56 MHz
UHF - 850-960 MHz

https://www.link-labs.com/blog/active-vs-passive-rfid

"Active: Active RFID tags cost between $5 and $15 each.

Passive: Passive RFID tags cost anywhere from $0.10 to $0.50 each."

"Can active and passive RFID tags work in tandem?
Yes! In fact, that’s something AirFinder is examining for the future. We’re currently looking into adding passive functionality into our active tags, for two reasons. 

First, it can provide time-sensitive chokepoint functionality, so we’ll be able to tell more accurately if a tagged item leaves a particular area. Second, it gives those who require active RFID scalability but could use passive RFID functionality a better option in the market. Stay tuned for updates!"

Home based BBS readers and digital signage devices could use passive RFID to "download data" without using any power, and an active RFID to transmit data.  

Today I realized my first internet service used a BBS-like email reader: " In August 1996, it began a free e-mail service — a customer would install the proprietary Juno client which would allow them to send and receive email of about 35 kilobytes in size. Version 1 did not offer attachments or other features. The user could write emails with the Juno client and would periodically sign in by dial-up. Upon doing so, the Juno client would upload any emails the user had written, download any new incoming emails in the online mailbox, and download targeted advertisements, which were displayed in the client. This was similar to "QWK" and similar less automated offline readers that had been used for years by BBSes to save phone line connect time.[citation needed]"

https://en.wikipedia.org/wiki/Juno_Online_Services

Unexpected discovery: When I visited the Wikipedia page of RFID, I did not expect that the first sentence would reference The Thing:

"In 1945, Léon Theremin invented the "Thing", a listening device for the Soviet Union which retransmitted incident radio waves with the added audio information. Sound waves vibrated a diaphragm which slightly altered the shape of the resonator, which modulated the reflected radio frequency. Even though this device was a covert listening device, rather than an identification tag, it is considered to be a predecessor of RFID because it was passive, being energised and activated by waves from an outside source.[8]" https://en.wikipedia.org/wiki/Radio-frequency_identification#History

------
Day 13
------
10:55 AM I will review the source  of https://www.i2phd.org/armradio/index.html After I downloaded it, i noticed it uses the same MBed software that I started this project with- the Keil compiler. So in my wandering, as Tolkien would say, I am not lost. I simply walked around the world and found different software along the way, one possibly more interesting than a file server. Obviously porting software would take time, and this is another project that may would need its own repository. 

Comparing ARMradio to the first microcontroller-based SDR that I found on Day 7 (the first that I googled, not necessarily the first that was developed), is where I should start this analysis. https://hackaday.com/2020/02/14/rf-shield-turns-arduino-and-pc-into-shortwave-radio/

In that, they used an Arduino, (although I may be wrong- I haven't located whether they used a microcontroller for all of the processing- the URL suggests the PC does that). Also, the other microcontroller from the IEEE article used an Atmega 2560, similar to the Discovery STM32F429 (the former is about $11 more at $41 US) and that's just for the central board, excluding any other hardware/RF. The Atemga is also designed for the VHF band 144MHz-148Mhz (whereas the ARM radio is 8kHz-900kHz), so they can't be compared exactly, though it is interesting that microcontrollers can/could process all of the DACs for transmitting and vice versa without an MMU. I'm still learning the lingo of analog and digital terms- i'm sure there is a word for Analog to Digital processors (maybe DSP is a generic/two way) for receiving signals. Edit: it's called ADC- i'm sure I read that somewhere. 

Update: it seems like Arduino-based SDRs have been around for more than 10yrs but with increasing processing power, are able to accomplish much more nowadays.
This also seems identify the name of analog to digital: https://hf5l.pl/en/sdr-z-arduino-nano/

"A “real” SDR radio is one where the RF signal received by the antenna is directly sampled by an analog-to-digital converter. Further processing of the signal takes place on the sequences of “ones and zeros”. However, other devices that use digital signal processing also fall under the SDR category. An example of this is the uSDX-RX receiver shown below, capable of receiving AM, FM, SSB (single-sideband modulation) and CW (telegraphy – Morse code) signals in a wide frequency range. The circuit is so simple that it can be quickly assembled on a universal PCB or on a prototype breadboard." 

That reminds me of the other, more recent article https://hackaday.com/2022/08/26/simple-breadboard-sdr-for-shortwave/ 10kHz-30MHz -quite bit of range!
 
One of my curiosities is whether there are any "shortcuts" to converting radio waves into digital signals without a sound card. Perhaps this approach already exists, and the technology was developed for retrofitting to PCs which already had sound cards, and it was more feasible to adapt computers to that, rather than developing a purpose built system on a chip. In the latter case, the tools to do that seem much more available today. 

I think I already found the answer to the previous paragraph: https://youtu.be/G8BIYIsh-4I?t=85

![image](https://user-images.githubusercontent.com/76194453/205982325-9cf76cf3-c254-433f-9f4b-8b65f95466aa.png)

Apparently a digital signal processor (often seen on MCUS) achieves the same functionality of a sound card. Whether that hardware is present on a typical mcirocontroller is a different question, but at least a distinction and comparison was made.

Some microcontrollers allow analog to digital conversian via SPI: 

![image](https://user-images.githubusercontent.com/76194453/205983016-fd539d2a-6b3a-4eb1-9bc4-7cb3873d4f84.png)

Whereas others may have built-in analog converters: 

![image](https://user-images.githubusercontent.com/76194453/205983449-636ff9e6-6ea2-413f-9ef9-89975d19e11d.png)

(Note: I am making an educated guess, so I'm 100% these could be used with relatively less hardware add ons)

DMIC: Digital microphone (Integrated Circuit?) board https://mcuxpresso.nxp.com/api_doc/dev/116/group__dmic.html DMICs don't appear to be very useful here, unless it is picking up audio from another device and converting it into digital- scratch that, They can be:

"Traditional microphones capture the sound you create in the air and pass this signal as an analog electrical waveform. For this output to make sense to your computer, it needs to be converted into a stream of discrete electrical voltages that correspond to 1s and 0s—this is a digital signal. USB microphones handle this process internally. Standard mics use a (male) balanced XLR connector to produce the analog electrical signal. There are also microphones that can output both analog and digital formats simultaneously.

...
So how do you connect a mic’s XLR to a computer? Well, that’s where a handy peripheral known as an audio interface (sometimes referred to by the legacy term “sound card“) comes in. Today we’re going to discuss USB and Thunderbolt audio interfaces in general terms. Firewire audio interfaces were quite common until recently and are readily available on the used market. We recommend avoiding these as many are no longer fully supported by the manufacturer or by current operating systems."

https://www.soundguys.com/what-is-an-audio-interface-23048/

Well, that was a helpful intro, though the XLR hardware pictured in that link is much larger than what's on an MCU- perhaps MCUs accomplish the same using smaller instruments?

LMIC: finding this acronym is proving to be more difficult. One search result appears to referenec Lora: LoraWAN-in-C, formerly LoraMAC-in-C https://docs.particle.io/reference/device-os/libraries/l/LMIC-Arduino/ 

AMIC: Analog Microphone (Integrated circuit?)  http://wiki.telink-semi.cn/tools_and_sdk/Driver/doc/kite/html/md__project_1__table_of__content_06__t_s_i__audio__features.html

Just now I found a list of <i>micro</i>SDX projects: https://gist.github.com/threeme3/9e447c291f64c19d65e3c91b9a1512b4

A hackaday tag https://hackaday.com/tag/software-defined-radio/ (115 articles) 

How do receivers pick up audio? An antenna. There are quite a few- active(powered), and passive ones. This is a type I have not read about before: http://www.pa3fwm.nl/projects/miniwhip/  https://www.sdradio.eu/weaksignals/SAQ/PA0RDT-Mini-Whip.pdf

http://websdr.ewi.utwente.nl:8901/ very interesting site! "On this page you can listen to and control a short-wave receiver located at the amateur radio club ETGD at the University of Twente. In contrast to other web-controlled receivers, this receiver can be tuned by multiple users simultaneously, thanks to the use of Software-Defined Radio." 


It seems like there is an inexpensive ESP8266 based transmitter: https://antrak.org.tr/blog/esp-wspr-simple-and-inexpensive-wspr-transmitter/ 

https://en.wikipedia.org/wiki/WSPR_(amateur_radio_software)

WSPR is very cool. From the above link, https://antrak.org.tr/projeler/bir-fisilti-wspr-macerasi-ve-esp_wspr/ translated from Google:

"WSPR Working Technique
Now let's examine the working technique of WSPR. WSPR data consists of three main pieces of information. Call sign, location, power. The call sign cannot exceed 6 characters in total. The first four characters of the Maiden Head Grid Locator data are used for the location. This gives us a position in an area of ​​100 square kilometers. Power is sent in dBm, so all sent information is a 50-bit string.

Your output power can be up to 5 watts. WSPR is a very slow communication protocol. The transmission speed is 1.46bps and it takes about 110 seconds to send all the data.

Each WSPR transmitter and receiver starts transmitting at the beginning of the even-numbered minute and finishes transmitting after 110 seconds. This time synchronization ensures that the start and end of each SPOT is synchronized with the transmitters and receivers.
Of course, I don't want to go into too much detail here. If you want to learn more about the protocol of WSPR data communication, I recommend the following site.
http://physics.princeton.edu/pulsar/K1JT/doc/WSPR/WSPR-main.html"

110 seconds isn't slow at all. Compared to John Cage's ASAP: https://en.wikipedia.org/wiki/As_Slow_as_Possible

"Organ2/ASLSP has been playing in Halberstadt for

21 years, 2 months, 4 weeks and 1 day"

"An organ in St. Burchardi church in Halberstadt in 2001 began a performance that is due to end in 2640. The next note will be played on February 5, 2024."

Notes, sounds, and radio waves. What do they have in common? Well, I'm enjoying the exploration of sound across the oxygenated medium of the earth's atmosphere that allows EMF. I'm kidding, I'm just using fuzzy logic here. But I'd like to visit the anechoic chamber in Minneapolis: https://www.atlasobscura.com/places/orfield-labs-quiet-chamber https://www.orfieldlabs.com/architecture/tour-video-tour-hold

While reading some history of radio, I found this interesting:

"Marconi applied to the Ministry of Post and Telegraphs, then under the direction of Maggiorino Ferraris,[34] explaining his wireless telegraph machine and asking for funding, but never received a response. An apocryphal tale claims that the minister (incorrectly named first as Emilio Sineo, later as Pietro Lacava[35]) wrote "to the Longara" on the document, referring to the insane asylum on Via della Lungara in Rome, but the letter was never found.[36]"
[36] Solari, Luigi (February 1948) "Guglielmo Marconi e la Marina Militare Italiana", Rivista Marittima

https://en.wikipedia.org/wiki/Guglielmo_Marconi#Transmission_breakthrough
Furthermore: 

"In 1896, Marconi spoke with his family friend Carlo Gardini, Honorary Consul at the United States Consulate in Bologna, about leaving Italy to go to Great Britain. Gardini wrote a letter of introduction to the Ambassador of Italy in London, Annibale Ferrero, explaining who Marconi was and about his extraordinary discoveries. In his response, Ambassador Ferrero advised them not to reveal Marconi's results until after a patent was obtained. He also encouraged Marconi to come to Britain, where he believed it would be easier to find the necessary funds to convert his experiments into practical use. Finding little interest or appreciation for his work in Italy, Marconi travelled to London in early 1896 at the age of 21, accompanied by his mother, to seek support for his work. (He spoke fluent English in addition to Italian.) Marconi arrived at Dover, and the Customs officer opened his case to find various apparatus. The customs officer immediately contacted the Admiralty in London. While there, Marconi gained the interest and support of William Preece, the Chief Electrical Engineer of the General Post Office (the GPO). During this time Marconi decided he should patent his system, which he applied for on 2 June 1896, British Patent number 12039 titled "Improvements in Transmitting Electrical impulses and Signals, and in Apparatus therefor", which would become the first patent for a radio wave based communication system.[37]"

I take a little inspiration from that. If, at first you don't succeed, look for other, more open-minded countries. :) 

3:38PM 

While it may sound pointless in describing the goal of this project despite straying from the direction that I set out to, I've found this concept to be quite consistent. Much like how the Age of Semiconductors allowed vast numbers of print media to be digitized in much smaller space, the dawn of low power transistors is causing a similar transformation in the system requirements to accomplish the same tasks. This article was 10 years ago: https://www.extremetech.com/computing/136043-intel-predicts-ubiquitous-almost-zero-energy-computing-by-2020

"This year, the company has discussed the shrinking energy cost of computation as well as a point when it believes the energy required for “meaningful compute” will approach zero and become ubiquitous by the year 2020. The company didn’t precisely define “meaningful compute,” but I think in this case we can assign a solid working definition. Adding two integers together is computing, but it isn’t particularly meaningful. Accurately measuring geospatial location via GPS, making a phone call, or playing a game is meaningful."

The Discovery board mentioned above, which is a board from 2014- uses260 µA/MHz at 180 MHz:

"Power efficiency: ST’s 90 nm process, ART Accelerator and the dynamic power scaling enables the current consumption in run mode and executing from Flash memory to be as low as 260 µA/MHz at 180 MHz. In Stop mode, the power consumption is 120 µA typical, which is 3 times lower versus STM32F405/415/407/F417.'

https://www.st.com/en/microcontrollers-microprocessors/stm32f429-439.html

The way I pursue research is like ARPA-E: "To focus on creative, transformation energy research that the industry cannot, or will not support due to its high risk, but that has high reward potential" https://en.wikipedia.org/wiki/ARPA-E
 
Some technologies are so disruptive that they may be limited only by their (current) obscurity. Sometimes it's normal to doubt oneself about whether something is a fad. But many of the early PC pioneers understood the long-game of computers. Energy engineering is a specific sub-field of engineering to improve the efficiency of generation of consumption of electronic products. https://en.wikipedia.org/wiki/Energy_engineering The main difference is that renewable power for decades has been relegated to stationary power plants (including offgrid), where soon wearables and consumer devices will be completely self-powered. The distraction of IoT marketing today is ignoring (either unwittingly or wittingly) the equally large, if not larger market of PioT (programmable internet of things): https://tibbo.com/programmable/modules.html (this is just one example) https://www.arm.com/glossary/iot-devices defines the term too.

If a technology were obscure, it could have an advantage for its owner- "security through obscurity." But technology also gains enhancements through convergence with other technologies. During the Edo period in Japan, the only port of trade open to the West was Dejima: https://en.wikipedia.org/wiki/Dejima "For 220 years, it was the central conduit for foreign trade and cultural exchange with Japan during the isolationist Edo period (1600–1869), and the only Japanese territory open to Westerners.[3]" In the early days of Unix computing, source code was accessible (part of the product), but it required expensive access to the hardware:
https://en.wikipedia.org/wiki/History_of_Unix#1970s
"In 1973, AT&T released Version 5 Unix and licensed it to educational institutions, and licensed 1975's Version 6 to companies for the first time.[12] While commercial users were rare because of the US$20,000 (equivalent to $100,717 in 2021) cost, the latter was the most widely used version into the early 1980s. Anyone could purchase a license, but the terms were very restrictive; licensees only received the source code, on an as-is basis.[12] The licenses also included the machine-dependent parts of the kernel, written in PDP-11 assembly language. Copies of the Lions' Commentary on UNIX 6th Edition, with Source Code circulated widely, which led to considerable use of Unix as an educational example" Libre Hardware (such as https://en.wikipedia.org/wiki/Open-source_hardware or https://en.wikipedia.org/wiki/CERN_Open_Hardware_Licence and https://www.fossi-foundation.org/2022/10/19/librecores,) that is- access to a technology, and its blueprints, is accessible via the internet. The large number of tech-evangelists (https://en.wikipedia.org/wiki/Technology_evangelist) or "missionaries" proselytizing new technologies that lead to more advances and breakthroughs (ones that I would not call Kurzweilian or exponential, but nonetheless accelerated) today exists because there is not a single port of entry to a culture.  https://en.wikipedia.org/wiki/Ray_Kurzweil#The_Law_of_Accelerating_Returns

I think the distinction should be made- when PCs first saw widespread consumer adoption- they did so because they were general purpose. Today, most MCUs are application specific. There is a high cost involved in general purpose microprocessor design, thus gap between power consumption of the lowest power MCUs and MPUs has not been closed. With time, general purpose application processors will allow a much larger developer (and userbase) to access and program energy autarkic processors, thus transforming the status quo of client/server based marketing. Why would users need to rely on a central service if they can communicate via smaller , local WANs?

A microcontroller that operates at 4uA/mhz is a 65x reduction in power from one that is at 260uA/mhz. Thus, this means one could have a portable radio that receives and displays/outputs information without a battery. That has never happened in over 120 yrs of radio. While not every hardware application could/should transition to a batteryless application, this new era of very low energy consumption for processing power ushers many new opportunities in hardware design. Practically anything on a microcontroller today could become batteryless, thus it's not too early to start thinking about batteryless (capacitor/solar li-ion capacitor) design of microcontrollers using a much larger  integrated system on a chip platform- energy harvester, radio receiver, transmitter, ADC, DAC, RTTY, and e-ink for low power displays. An all in one that would not require any external cable to charge (but rather optional). 

It's as if I were writing on a BBS in the late 80s and suggesting one could fit a camera on a brick phone, when the idea would be a reality by 2001: the Nokia 7650: "Feature-rich, it was the first phone with a built-in camera (VGA resolution), and thus its imaging capabilities was widely marketed" https://en.wikipedia.org/wiki/Nokia_7650

Thus it's hard to imagine a standalone autarkic radio player today fitting on a solar powered mobile device, but if Moore's Law is any indicator, a JVC VHS grade camcorder eventually made its way onto a phone, so this is the kind of mentality it takes to accept the idea that even more things can fit on a handheld device today. A phone that doesn't need charging? I'm willing to bet if it took 10 years to from conception to put a camera on a phone, it could take 10 years to develop a phone without batteries. By 2032, batteryless phones will be widespread. I'm willing to bet $5. But it's not going to look like today's phone. It's going to transmit as much text as a phone from 1997: https://en.wikipedia.org/wiki/Nokia_6110 I think that it could be ready by 2025.

Power can be creted in multiple ways: thermal harvesting: https://e-peas.com/product/aem20940/  thermoelectric generator (TEG), ambient RF signals:  https://e-peas.com/product/aem30940/ AEM30940 Vibration Energy Harvesting  https://e-peas.com/product/aem30940-2/ and solar https://e-peas.com/product/aem10941/ 

Some of these harvesting techniques may interfere with the ability to collect shortwave radio, such as RF (my guess), although nothing suggests the hardware cannot be shielded from itself to allow discrete functions.

The digitization of print certainly caused a transformation in economics. Batteryless hardware could lead to completely new wireless networks, both public and private, and may also result in more consumer-oriented services-. Setting a data cap is obviously an economical decision- the revenue to maintain an infrastructure has to meet some ROI, although in many cases this may have already been achieved by larger telecoms. That said, LoRa wan networks could potentially offer community based internet at much more limited scale- https://lora-alliance.org/lorawan-news/why-lora-will-be-the-likely-winner-in-lightweight-wan-battle/ the reasoning here is that the cost of hosting or relaying information, could be shared by the members. Bands would obviously need to be negotiated with public aiwaves, but the concept that a co-op of hosters could serve as a mesh network using solar powered routers allows the internet as we know it to be further decoupled from the electric grid and to enable more resilient/antifragile communication.

"In the mid 1890s, building on techniques physicists were using to study electromagnetic waves, Guglielmo Marconi developed the first apparatus for long-distance radio communication.[1] On 23 December 1900, the Canadian inventor Reginald A. Fessenden became the first person to send audio (wireless telephony) by means of electromagnetic waves, successfully transmitting over a distance of about a mile (1.6 kilometers,) and six years later on Christmas Eve 1906 he became the first person to make a public wireless broadcast.[2][3]"


