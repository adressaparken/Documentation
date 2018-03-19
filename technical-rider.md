# Technical rider

Summary

Please use this summary as a checklist for Adressaparken.

The technical section is part of the contract and you are responsible to comply with its requirements.

As a working procedure adressaparken encourages visits to the installation site as long as notice is given.

Any changes or deviations from the technical specifications of the contract rider, must be approved.



If there are any questions, problems or difficulties complying with any aspect of the following requirements please contact:

  


Andrew Perkins, andrew.perkis@ntnu.no

**Trondheim, 01 September 2017**

  
  


---



**SECTION 1 – TECHNICAL RESPONSIBILITIES**



**HEALTH AND SAFETY**



**Electrical and Other Appliances**

The power in Norway is 230V generally distributed through [shucko](https://en.wikipedia.org/wiki/Schuko) plugs. Electrical equipment provided by guests should comply with local requirements and be inspected prior to installation.

Any equipment installed in public space should be in accord to local universal access regulations.



**Rigging Operations**

In all instances pertaining to rigging safety, Adressaparken’s technical personnel is responsible for determining appropriate measures to be taken. Any person undertaking any rigging at Adressaparken must hold a certificate of competency appropriate to the skill level required as issued by a recognised authority and/or have experience in this type of operation. Only rigging devices engineered, certified and rated for the task may be employed.

Any rigging to be done outside of the park area will depend on permits from local authorities.

**  
**

**Media Equipment**

All media equipment available onsite is listed below in this document and free for use by guests. On dealing with sound installations in the park, care must be taken so it doesn't disrupt the nearby activities.

**  
**

**Security**

The sandbox media infrastructure at Adressaparken is completely open in local network. Care must be taken on creating access points that could be potentially misused by the public.

**  
**

**Working procedures**

The server running in the control room is the gateway for all communications in the park and it is also responsible for storing and presenting all the sensor data to the web. We strongly advise against using this if not strictly necessary.

Changelogs must be kept as appropriate so system can be reset after guest visits. We do also recommend system backups to be made before guests commencing development in the local machines.



---



**SECTION 2 – GENERAL OVERVIEW**



**Network**

A single Ubuntu machine acts as DHCP server and gateway for the local network.

All hardware part of the main installation will have assigned IPs, any locally connected machine will be automatically assigned an IP address \(192.168.1.150-200 : 255.255.0.0\).

NOTE: There is no wireless access in the control room.**  
**

**Sensors Overview**

The area of the park is covered by a scalable infrastructure for media installations, offering power and data infrastructure site wide. In addition there are available the following sets of actuators and sensors as part of the fixed installation. If need to reconfigure please advice with Adressaparken responsibles.

**  
**

**Local Sensors**

9 x Raspberry Pi nodes running each an openCV based motion detection system and also featuring temperature, light and sound sensors. The data of this system is published system wide as MQTT and / or OSC packets and available for realtime use. The system is based on a [Raspberry Pi 3](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) with [noIR v2 Camera](https://www.raspberrypi.org/products/pi-noir-camera-v2/), [enviro phat](https://shop.pimoroni.com/products/enviro-phat) and USB microphones. A complete BOM is available in the Adressaparken Dev Document.

**  
**

**Media Control**

All control data in the infrastructure is done over [OSC](https://en.wikipedia.org/wiki/Open_Sound_Control) protocol. This means to be easily expanded and open for all nodes. Exception is made for the libelium system which is made available through the WEB API description.



**Signal and Power Distribution**

Signal distribution is available from control room to weatherproof boxes onsite \(Type 2, see diagram in theSection 3 - Equipment Listor through the [link](https://www.dropbox.com/s/ghvep2qklfr6lp3/park%20layout.png?dl=0)\), namely for XLR 5 \(DMX\) and RJ-45 \(Ethernet\) connectors. The XLR 5 connectors can potentially be used as a cable link between the park and control room.

Video feeds are also available for using with either screens or projectors in the park.

Additional power sources and extra distribution equipment are widely available through the park and should be negotiated on a project basis. Please follow the[ link](https://www.dropbox.com/s/035mc3y8hauur0i/Sensorboks-innredning.pdf?dl=0) for a box design description.



**Libelium System · Web API**

A separate sensor system \([Libelium Smart Cities Pro](http://www.libelium.com/new-smart-cities-platform-air-quality-dust-sound-light-precision-sensors/)\) offers additional information on environmental data onsite, refer to manufacturer for development guides and the development document for details on local specification. The data from the system is stored in a mySQL database in the server and available online through the WEB API [link](https://parken.perseum.com).



---



Adressaparken does not guarantee that all or any of these facilities or equipment will be available or suitable for the purposes of the guests. Please contact to ensure the information contained herein is up to date and correct.

The equipment list is a total list for the park

Find this image in the following [link](https://www.dropbox.com/s/ghvep2qklfr6lp3/park%20layout.png?dl=0)

**ONSITE ACTUATORS**

Light / Sound / Video

· 10 x Analog RGB LED strips built onto floor, fixed

· 6 x Omnidirectional speakers, fixed \(Bose Freespace 51[link](https://www.bose.com/en_us/products/speakers/stereo_speakers/free-space-51-environmental-speakers.html)\)

· 2 x Video Projector PT-RW630[link](http://www.projectorcentral.com/Panasonic-PT-RW630LBU-projection-calculator-pro.htm)

NOTE: Extra speakers and screens can be accommodated in the system. However, current setup only caters for a total of 6 passive speakers.

**CONTROL ROOM**

Control

· 1 x HP ProLiant DL380 Gen 9 [link](https://www.hpe.com/h20195/v2/GetPDF.aspx/c04346247.pdf)

· 2 x Mac Mini 2014 with screen, keyboard and mouse

· 2 x PC with screen keyboard and mouse \(updated specs on request\)

· 2 x Extreme Summit x450

Media

· 1 x MOTU AO24 soundcard [link](http://www.motu.com/products/avb/24ai-24ao)

· 3 x Stageline STA 400D amplifiers \(total 6 channels\) [link](https://www.img-stageline.com/products/audio/pa-amplifiers/digital-pa-amplifiers/sta-400d/)

· 1 x Hippo Karst [link](http://www.green-hippo.com/hippotizer-media-servers/karst/)

\(not installed but available\)

· 1 x KVM Switch 4 Port [link](http://www.kvm-switches-online.com/cs1644a.html)

· 1 x 2:16 HDMI Switcher [link](https://www.leteng.no/avdelinger/produkter/av-switch--and--scaler/hdmi/kramer1/kramer-switch-2x1-16-hdmi-19-675gbps-rs232-ir-edid-re-k-hdcp-vm-216hdmi-p0000015571)

NOTES:

· Video is routed through 3 x HDMI extenders and available in the park.

· Sound to the soundcard can be sent over USB or DAC, output is routed through 3 x amplifier and feeds the 6 speakers installed.

· Lights are controlled by either the Hippo Karst or an installation of M-PC and sent to an ENTTEC Artnet decoder \([link](https://www.enttec.com/eu/products/controls/legacy/ode/)\), which is not accessible

  
  
  
**  
**

