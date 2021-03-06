# Development Guide

All Repositories and assets can be found listed below, note that not all might be publicly open.

2 - Media Playback

3 - Raspberry Pi

* [Sensor + OpenCV](https://bitbucket.org/parken_dev/raspberry-pi-python-app)

4 - Sensor API - Libelium

* [API](https://bitbucket.org/parken_dev/parkenwebapi)
* [Website](https://bitbucket.org/parken_dev/parkenweb)
* [Libelium](https://bitbucket.org/parken_dev/parkenlibelium)

**General Architecture**

The system at Adressaparken structures itself around independently acting nodes, both of sensors or actuators. As a general guide, the system is designed so that all of the nodes are open to be used as inputs or outputs for the data. The artist's work positions itself accordingly so it can use relevant inputs / outputs to the work.

The local system is completely closed, with a server acting as gateway for all outside communication. Ensuring that all communication can navigate openly inside the local network.

Exception to this is the Libelium system, a set of environmental sensors.

The data from this sensors is stored in an internal DB \(in the server\) and available online through a node.js API.

## **SECTION 2 – Media Playback**

The installed media server is capable of playing multi track audio, 3 outputs of video and outputting Artnet. Meaning it has capacity to run all the actuators in the park natively. Adding to the fact that it can be controlled with several show network standards \(DMX, OSC, MIDI, TCP, TIMECODE etc.\) it makes for an ideal backbone for interactive installations.

Hippotizer has a big user base and is well documented, please visit the [online manual](http://www.green-hippo.com/manual/), [forum](http://forum.green-hippo.com/) or [youtube videos](https://www.youtube.com/user/HippoSchoolOnline) for more information.

Video over Network

Having said that, there might be situations where a separate machine is needed. For this, any of the other machines could be used. If the user still wants to use Hippo it is possible to route video through Spout, NDI or other networked video solutions. For Windows machines Hippo offers its own system: [ScreenThief](https://support.green-hippo.com/article/2-software-downloads).

Creating content for Hippotizer

Any of the following formats can be used within Hippo, the server also has internal encode on import functions. ****

Video \(minimum size 64 x 64 pixels\)

| Codec | Extension |
| :--- | :--- |
| Mpeg4 | .mp4 |
| ProRes422 | .mov |
| ProRes420 | .mov |
| ProRes444 | .mov |
| ProRes4444 | .mov |
| FlexRes | .fxr |
| AVI | .avi |
| Animation RGB | .mov |
| Animation RGB + Alpha | .mov |
| H264 | Varies |
| HAP | .mov |

Images, including image sequences \(minimum size 64 x 64 pixels\)

| Codec | Extension |
| :--- | :--- |
| Tiff | .tiff |
| PNG | .png |
| JPEG | .jpg |
| Targa | .tga |

Audio Encoding

| Codec | Channels | Bit Depth |
| :--- | :--- | :--- |
| Wav | 1 | 16b |
| Wav | 2 | 16b |
| Wav | 4 | 16b |
| Wav | 6 | 16b |
| Wav | 8 | 16b |
| Wav | 2 | 24b |
| Wav | 2 | 32b |
| MP3 | 2 |  |

Media Server Control

The Media server can be controlled with use of several industry standard protocols. See [Multicontroller](https://www.green-hippo.com/manual/hippotizer-v4/4.2/en/topic/multicontroller) in the products manual.

Lighting and Sound

Any of the other computers can be use for more specific playback of lighting and sound sequences. While there are no sound specific software installed, PC 1 has a M-PC installation that is ready configured for use. of the following formats can be used within Hippo, the server also has internal encode on import functions.

Sound over Network

The installed soundcard supports AVB \(Audio Video Bridge\), a protocol that can be used for transmission of audio over the network. Unfortunately it seems to be blocked by the switch, and only work in OSX environment. Please see the MOTU’s [user guide](http://cdn-data.motu.com/manuals/avb/24Ai_24Ao_User_Guide.pdf) for detailed information or use this [Mac Guide](http://motu.com/avb/using-your-motu-avb-device-as-a-mac-audio-interface-over-avb-ethernet/).

Notes on offline preparation

Hippotizer has an [offline system](http://www.green-hippo.com/hippotizer-media-servers/play-licensing/) available for free download. All setups made in the offline system are fully compatible with the system installed. While this does not offer any video output it is a perfect way to prepare setups before arriving to the park.

## **SECTION 3 – Raspberry Pi \(openCV network\)**

The collected data is published via OSC and MQTT within the system.

`The OSC addresses are as following:`

* `/rpi/<RPi-ID>/temperature`
* `/rpi/<RPi-ID>/pressure`
* `/rpi/<RPi-ID>/light`
* `/rpi/<RPi-ID>/pedestrian`

The messages are broadcast using the network's broadcast address and the port can be specified for each Raspberry Pi individually in the control panel \(covered in detail further down in this document\).

The data is also broadcast using the MQTT protocol, which is also used for system specific purposes, e.g. heartbeat messages, etc.

`The MQTT topics are as follows:`

* `parken/rpi/<RPi-ID>/version- current version number of the app`
* `parken/rpi/<RPi-ID>/quit- halts the program`
* `parken/rpi/<RPi-ID>/restart- restarts the Raspberry Pi`
* `parken/rpi/<RPi-ID>/heartbeat- heartbeat sent every 10 seconds`
* `parken/rpi/<RPi-ID>/settings- used to change settings in the RPi`
* `parken/rpi/<RPi-ID>/temperature`
* `parken/rpi/<RPi-ID>/pressure`
* `parken/rpi/<RPi-ID>/light`
* `parken/rpi/<RPi-ID>/pedestrian`

Control panel for Raspberry Pi’s

The control panel for the Raspberry Pi’s is written in javascript using the node.js and express frameworks. It can be accessed with a web browser on [http://192.168.1.1:8080](http://192.168.1.1:8080)

It is comprised of a global tab and an individual tab for each Raspberry Pi. The global tab has a list of all the connected Pi’s and their status \(online or offline\) as well a a form for changing settings globally. The individual tabs show a list of the Raspberry Pi’s last published data as well as a form to set the individual settings. The possible settings are as follows:

* OSC port - port via which the OSC messages are published
* For each sensor and the openCV data:
* * Checkboxes if the data should be broadcast on change and/or on an interval
  * The duration of the interval and the threshold for the change

As described earlier, the Raspberry Pi’s publish a heartbeat every 10 seconds. This is comprised of the Raspberry Pi’s ID and the current settings. Once a new set of settings is received, they are updated internally and the new settings will be broadcast.

## **SECTION 4 – API \(Environmental Sensor Network\)**

The newly installed [Libelium](http://www.libelium.com) system is a custom spec based on the [Plug and Sense - Smart Cities Pro](http://www.libelium.com/products/plug-sense/models/) package.

This API makes available data stored from multiple sensors \(humidity, temperature, CO2, etc...\) installed in a Park.

Please refer to manufacturer for detailed documentation and guidelines and the bitbucket [repository](https://bitbucket.org/parken_dev/parkenlibelium) for details on the code.

The current installation has the following sensors:

* Plug & Sense! SCP WiFi
* 9370-P Temperature, Humidity and Pressure Probe
* NLS Noise Level Sensor
* 9372-P Carbon Dioxide Probe
* 9387-P Particle Matter \(PM1 / PM2.5/ PM10\) - Dust Probe
* 9375-P Luminosity Probe ****

Procedures are documented in the API description [here](https://adressaparken.no/#cbp=apireference/api_overview.html).

