# catears

This repository contains everything you need to build your own brightly lit cat ear hairband with widely adopted electronics.

## Why?

This project got inspired by the satirical "Safety cat ears required" signs you might see in some hackspaces or at chaos events. Half joking I once said I will actually build "real" safety cat ears. This repository is the result of that.

## Build your own ones - Step by step!

### Item List

You will need the following items:

- Part 1 & 2 from the `models` folder printed with any 3D printer
- 1x ESP8266 (I am using a "Wemos D1 Mini")
- 1x a few centimeters of a WS2811 LED strip 
- A bunch of cables to solder everything together
- A Micro-USB to USB cable
- A USB power source (e.g. a power bank)

Further, access to the following tools is needed:

- A soldering station/kit
- A computer with docker for the initial setup

#### Alternative Hardware

You totally can use other hardware components - some notes on swapping parts:

**Microcontroller**

Every microcontroller supported by ESPHome should work. At least 1 GPIO pin should be accessible. Using a different microcontroller requires adopting the ESPHome config.

**LED strip**

Looks best with a silicon diffusor on top - strips are available with a pre-applied one. Search for "COB" or "FCOB" LED strips with the WS2811 chip set.

You can use any other LED strip supported by ESPHome and the neopixel integration. However, using a different chip set requires to adopt the ESPHome config accordingly.

The 3D models are designed to accomodate a 12mm wide LED strip with a 2.65mm wide silicon diffusor on top.

#### Fitting the 3D printed Hairband

You can scale the hairband according to your needs. I seem to have a pretty big head, so the supplied model already is pretty large. It is roughly 20% larger than the "usual" cat ear hairbands in my hackspace. 

To scale the models import them into your favorite slicer and scale the x/y axis for the same amount (do not touch the z axis/height).

### Putting it together

1. Print the hairband. Part 1 & 2 are needed.
2. Solder wires to your LED strip and connect them with the microcontroller.
   1. You can use a connector between them to easily plug and unplug them.
   2. The LED strip runs on 5V.
   3. Connect the data wire of the LED strip to your microcontrollers `GPIO3` pin.
3. Assemble the models.
   1. Put the LED strip into the thin groove along the top of the hairband of the bigger of the 2 models.
   2. Cut the LED strip to size.
   3. Put the second, smaller part o top and make sure the LED strip is fitting into its groove as well.
4. Flash the microcontroller.
   1. Copy `esphome/secrets.example.yaml` to `esphome/secrets.yaml` and set your secrets.
   2. Connect the microcontroller to your computer via a USB cable.
   3. In a terminal run `(cd esphome && docker compose up)`
   4. Navigate your browser to `http://127.0.0.1:6052`.
   5. LogIn with user `admin` and password `admin`.
   6. Using the UI upload the `catears.yaml` to your microcontroller.
5. Verify everything is working.
   1. Power the microcntroller (either by your computer or an external power source).
   2. Navigate your browser to `http://catears.local/`, the ESPHome dashboard should be visible.
   3. You can change the brightness, color and effects from this dashboard.
