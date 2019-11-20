# Internal

SECTION 1 – Server

The Server at Adressaparken acts as a gateway for all communications but it does not have an active input in any of the processes. Its main services are the following:

· Gateway to web connection

· DHCP server for local installation

· Storing and serving of Libelium sensor data through the Web API

· Presenting web API website

· Monitoring local network status

Configuration

The server is running an installation of Gnome Ubuntu 16.04

NOTE ON NETWORK ADDRESSES:

The DHCP configuration assigns fixed IP addresses for the main machines that run the installation \(2 x Mac mini, 2 x PC, 1 x Media Server\), while we recommend the use of static IP addresses where possible, all new machines to the system will be given an IP address on the 192.168.1.x range.

Links provided are purchasing suggestions in Norway \(where possible\). The assembly tries to be as simple and generic as possible, making for easy tinkering and expansion.

Code Repositories

Development for the Raspberry Pi units was done in Python with maintenance and config code in Node.js.

· Raspberry Pi code \(in[ Bitbucket](https://bitbucket.org/parken_dev/raspberry-pi-python-app)\)

· Server side code \(in [Bitbucket](https://bitbucket.org/parken_dev/raspberry-pi-control-panel)\)

**Python code for sensor data and OpenCV**

The ****code running on the Raspberry Pi’s that gets sensor data from the attached sensor board and detects people with openCV is written in python3. The sensor board, EnviroPhat by Pimoroni, comes with a temperature-, pressure-, light- and motion-sensor, as well as 5 analog inputs, which can be used to add more sensors. The motion sensor is not in use for this project, as the Raspberry Pis will be stationary and it would be futile. There is a separate thread in the python code, that continuously receives the values from the sensor board and stores them locally. Depending on the settings \(covered in more detail the next part of this documentation\), the sensor data is transmitted regularly or whenever it changes or both.

The openCV code also runs in a separate thread. It captures images at a resolution of 640x480 pixels, then crops the left and right edges, so 2 adjacent cameras don’t cover the same area. The framerate is set to 32 frames per second and the shutter speed and ISO values are set at runtime, depending on the surrounding light levels. A background subtraction algorithm, that comes with openCV, is used to reduce the false positive rate for the detection. Each frame is compared to the previous frame and the openCV detection algorithm will only be applied if there was a significant change in the frames. This reduces the overall processing time and makes the system more reliable. Generally a single frame can take up to 400 milliseconds to process on the Raspberry Pi, so the less frames are processed, the better.

Data Storage and API link

All data from Libelium is stored in the local server \(192.168.0.1\) in a mySQL database. From here the data is made available through our REST API hosted in the same server.

