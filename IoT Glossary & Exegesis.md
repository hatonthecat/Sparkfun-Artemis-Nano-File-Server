This is a Glossary of IoT terms I have encountered, in order of first encounter.
---------------------------------------------------------------------------------

Internet of Things- devices that connect to the internet, typically without a face or human interface device. There are so many of them, someone foresaw the need for IPv6 addresses.

Ubiquitous Computing - Computing that's everywhere. Enough said? That was a joke.

Ambient Computing -used interchangeably with "ubiquitous computing"- using a computer that is so quiet one doesn't realize they are using one. See Brian Eno's Music For Airports: http://slashseconds.org/issues/001/001/articles/11_psuchin/index.php

Energy-scavenging - it looks for power in the nearby environment, used in an anthropomorphic and imperfect analogy. 

Energy-harvesting - able to produce power locally/off-grid to power the device (agnostic as to partially or totally), as if it is some kind of farmer (also anthropomorphic, incongruously compares months of work into hours or minutes, if comparing the time it takes to grow food crops to generate power from a photovoltaic panel or thermoelectric generator) https://en.wikipedia.org/wiki/Energy_harvesting

Energy-autarkic- similar to energy-scavenging and harvesting, but more specifically reveals/indicates that the device requires no external charging, or possibly even batteries (as with capacitors/li-ion capacitors). It also is the least personified. This does not refer to the energy needed to manufacture the device, which a given, but post-imaging of the binary and once it is in a "production environment."

For the technically minded, I prefer the 3rd -"autarkic" because it sounds more "correct" (depending on the application), but for those explaining to the non-technical, and for those applications/users that are agnostic, or lazy, you can use the the first two.

Pervasive Computing - What? Seriously?? 
This is a blend of two concepts- ambient computing- computing that is available under the threshold of awareness, and ubiquitous computing- computing that is everywhere and is being used all the time, because it is impossible to know if it is even on and where they are scattered, like land mines from WWII.
Proceed cautiously and be mindful of the environment when developing new products. Please do not use the words "disposable" and "electronics" in the same sentence. To be clear, ubiquitous computing is already here- it's just that if there is going to be an inevitable rise in number of connected devices, it should not sprawl without at least some kind of planning. Designing micocontrollers that can be repurposed should be a development goal. Single use, and hard-to-recover from the exosystem should not.
This paper explains the term better than I can: 

https://brandenghena.com/projects/lpwan/ghena19lpwans.pdf

p.6 "The single location metrics show the requirements to deploy an instance of each application, while the pervasive metric assumes that the application is deployed at scale in its target environment." 

Additional projections: "When NVIDIA purchased mobile-chip designer Arm Holdings from SoftBank last year, NVIDIA CEO Jensen Huang made the bold prediction that in the years ahead, there will be trillions of artificial intelligence (AI)-enabled Internet of Things (IoT) devices." https://cacm.acm.org/magazines/2021/7/253454-a-battery-free-internet-of-things/abstract

OTA- Over-the Air updates- Not a chronological encounter, but a a catch-all term for all wireless communication to boards incluing IoT and LTe cell networks. It's a very broad term, but doesn't get much scrutiny. The reason is, "over-the-air" is a software term aimed at developers, who are either agnostic or afraid to know of the frequency. The term is going to fly over the heads of non-technical users, so it does not really serve much purpose in the highly technical research and development field. Instead, I propose OTA be replaced with:

OTA433 -LoRa @ 433Mhz
OTA800  -GSM @ 800Mhz
OTA1800- -GSM @ 1800/1900Mhz
OTA2.4GHz - WiFi/Bluetooth

This is a more specific designation of OTA. OTA attempts to simplify a method of updates with a generic term, but it raises more questions than it attempts to answer. Perhaps it aims to reach some kind of middle-ground- for those who are not privy/interested in the frequency, but to convey awareness of the wireless medium. In Stephen Pinker's <i>The Stuff of Thought</i> (2007), a similar phenomenen exists in the English language. "If you could pass the salt." It means nothing but it avoids the apparent aggressivenes of "Can you pass the salt" and replaces it with the passive-aggressiveness of "If you could" with no proposed outcome of the "If". "Over the air", likewise, is "If you could update OTA, period", without stating <i>how</i>. That is how much OTA makes sense. But use it if your crowd is neither technical nor technical. I'm sure someone wants to hear the buzzword. Most cell phones have at least 2 radios- Wifi and LTE, thus OTA isn't really interested in how, other than air. When developing a single-radio solar powered mobile device, presumably to save power, the type of radio makes all the difference. 

-------------------------------
-------------------------------
Free-form commentary

-------------------------------
-------------------------------

For wireless networks, using too little throughput requires the device to be running constantly. Using too much throughput increases the storage requirements. Having a balance of economy and conciseness of information transfer should be a goal of communication protocols that transmit essential services.

Autarkic computing can be used as a counterbalance to pervasive computing, if, and only, it is not scaled up to unsustainable levels. Imagine, on a quadrant of of low and high bandwidth and power. Say, in Quadrant I and IV, you have high bittrate, but Quadrant I is irrespective of power consumption. Quadrant II and III is low bittrate, but QII is high consumption. Quadrant III is low power consumption, and Quadrant IV is high power consumption, low bittrate (old and inefficient devices). Thus, the Positive X-axis is high data throughput, and the positive Y axis is high power consumption. Autarkic Computing could be used to operate in Quadrant III, whereas improvements in transistor nodes (Moore's Law), increases in throughput could relatively place more throughput currently in Quadrant I, II and IV into Quadrant III over time. 

IoT - Internet of Things is a curious choice of words, even though it is a plainly obvious meaning. Why not "Internet of People"? Perhaps since there is already hardware for "people," there is less of a need to emphasize user interfaces. It would be interesting to develop this project as part of a story. The book Foucault's Pendulum, by Umberto Eco, comes to mind. What if the purpose of this project, were a reaction to the Internet of Things? For example, if I wanted to bet that IoT devices will be manufactured in the billions a decade from now, then it would be somewhat reasonable to develop a guarded view that IoT may end up taking over our way of life, for better or worse. Obviously, IoT devices are in their infancy right now (in 2022), and have no advanced AI, even if a cloud is able to gather substantial data. Therefore, the motivation of this project is to begin a playful competition between IfT- the Internet <i>for</i> things, and IfP- Internet for <i>people</i>. 

There are multiple ways one can embark on this project. The first, is to do nothing, and to wait patiently for 10 years, and then to panic if a swarm of IoT devices amassed a hive mind and developed Artificial General Intelligence.

Another option is to begin developing arbitrary and useful software that humans can understand- layman tutorials, so that if IoT devices ever developed superintelligence, humans would have substantially more hacking tools to modify the firmware of a number of microcontrollers. If IoT devices are invading the consciousness, then programming IoT devices is the counterinsurgency. As developing and producing IoT devices becomes more popular/accessible, the demand for IoT devices could shift from being used to serve large organizations to serving individuals or the collective. I am reminded of the 2007 game BioShock by 2K Games (not the weird Infinite Sequel), where parts are unlocked for hacking vending machines and reverse-programming drones. If there are no tools to do this in 2032, how helpless will humanity be in Rapture?   

![TheFlamingLips-YoshimiBattlesThePinkRobots](https://user-images.githubusercontent.com/76194453/203817273-21fa52b2-dcdf-42d5-b84e-05b08813e68e.jpg)
