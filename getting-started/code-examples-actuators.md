# Code examples - Outputs

The park makes available an array of actuators \(lights, sound a video\). This are easily expandable using the built in infrastructure.

For detailed information on the equipment please visit the Technical Rider

**Lights**

The lights are controlled via Artnet, an UDP transport for DMX.

**Sound**

Sound is simply connected via USB from a computer to the soundcard. Once the connection is checked you can use any sound player software of your choice or generate your own as in the example below

**Python example with sound and light:** [https://github.com/adressaparken/adressaparkendemo](https://github.com/adressaparken/adressaparkendemo)

**Video**

The video in the park is played through a Karst Media server, control is setup over Artnet but it can be used over several industry protocols. Please see how to create content for the [screen directly](led-display/content-raster.md)

