# System Overview

**Network**

A single Ubuntu machine acts as DHCP server and gateway for the local network.

All hardware part of the main installation will have assigned IPs, any locally connected machine will be automatically assigned an IP address \(192.168.1.150-200 : 255.255.0.0\).

NOTE: There is no wireless access in the control room.    
****

**Sensors Overview**

The area of the park is covered by a scalable infrastructure for media installations, offering power and data infrastructure site wide. In addition there are available the following sets of actuators and sensors as part of the fixed installation. If need to reconfigure please advice with Adressaparken responsibles.

**Local Sensors**

9 x Raspberry Pi nodes running each an openCV based motion detection system and also featuring temperature, light and sound sensors. The data of this system is published system wide as MQTT and / or OSC packets and available for realtime use. The system is based on a [Raspberry Pi 3](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) with [noIR v2 Camera](https://www.raspberrypi.org/products/pi-noir-camera-v2/), [enviro phat](https://shop.pimoroni.com/products/enviro-phat) and USB microphones. A complete BOM is available in the Adressaparken Dev Document.

**Media Control**

All control data in the infrastructure is done over [OSC](https://en.wikipedia.org/wiki/Open_Sound_Control) protocol. This means to be easily expanded and open for all nodes. Exception is made for the libelium system which is made available through the WEB API description.

**Signal and Power Distribution**

Signal distribution is available from control room to weatherproof boxes onsite \(ADD IMAGE\), namely for XLR 5 \(DMX\) and RJ-45 \(Ethernet\) connectors. The XLR 5 connectors can potentially be used as a cable link between the park and control room.

Video feeds are also available for using with either screens or projectors in the park.

Additional power sources and extra distribution equipment are widely available through the park and should be negotiated on a project basis.

**Libelium System · Web API**

A separate sensor system \([Libelium Smart Cities Pro](http://www.libelium.com/new-smart-cities-platform-air-quality-dust-sound-light-precision-sensors/)\) offers additional information on environmental data onsite, refer to manufacturer for development guides and the development document for details on local specification. The data from the system is stored in a mySQL database in the server and available online through the WEB API [link](https://parken.perseum.com).

