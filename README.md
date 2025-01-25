# Trebuchet

The Trebuchet is a DIN rail mountable IO module which can be connected to the [Onager](https://github.com/Feudal-Project/Onager) module (controller). It is intended as a DIY project for anyone who is already familiar with ESPHome and has a basic to advanced level of soldering skills.

## Features

- 16 24V inputs

- 16 24V low side switching outputs functioning as relay drivers (integrated flyback diode).

- Side connector for daisy chaining up to 4 trebuchet modules.

- Galvanically isolated input and output rows to prevent cascading damage throughout daisy chained devices.

- 3D printable housing with engraved port descriptions and DIN Rail compatibility with 3D printed locking keys.

- Highly versatile in its use due to the vast possibilities of ESPHome.

<p align="center">
  <img src="/images/Trebuchet.jpg" width="50%">
</p>

## Background
In 2023 I had the opportunity to work on a smart home for a house being newly built at that time. The owner is a big fan of Home Assistant and the general concepts of the local smart home as well as open-source soft- and hardware. We discussed many options. Simple WiFi and Zigbee relays (like shelly and others), as well as wired approaches (like KNX) were taken into consideration. We agreed that a wireless setup would not make use of the potential a newly built home provides. Wired bus-based solutions like KNX, would lock him in forever and a truly “dumb home” would from there on not be possible as you have to rely on the bus routed throughout your home. The only type of solution which came close, was to use a lot of shelly pro devices (DIN rail mountable shellies) and wire all lights/blinds/etc. back to the control cabinet. Such a solution would “hardwire” input switches to specific devices though. While calculating the cost of using shellies, I came up with the idea of creating an ESPhome based solution. Basically an ESP32 on steroids making use of dozens of IOs. We settled on using ESPHome not only because of the price difference but also because I always wanted to create such a behemoth of a system.

## Buying guide for the Trebuchet

This section will be completed soon! Come back later to see how and where you will be able to get all necessary components for creating your own Trebuchet module!

## FAQs
### Who is the Feudal project for?
It’s for people who:
- want to have a fully local smart home.
- want to have an open source smart home.
- want to have a central smart home and are willing to wire everything necessary towards that central point (or multiple, if you scatter the controllers around your home).
- want to have a smart home with ESPHome at the core, with all its perks and problems.
- want a DIY smart home, to fully create a unique experience.
- are prepared to take responsibility for the functionality of their smart home and are aware of their accountability towards the other residents of the home.
- don’t have a fundamental problem with things needing a bit of tweaking and maintenance now and then.
- are able to test as much of their setup before it gets implemented into the house.
- have basic to advanced skills in soldering and have already successfully completed a few ESPHome projects.
- do have a 3D printer or at least know how to get things printed elsewhere.

Do you recognize yourself above? That’s great! You should be good to go for this project! If not, just tell me about your concerns in the [Q&A discussion section](https://github.com/Feudal-Project/Trebuchet/discussions/categories/q-a), I will try to help you to make the right decision!

### What is the idea behind the Trebuchet?
The main idea is to connect any appliance controllable by a switch, and any type of sensor providing a binary output to this module. The ESPHome configuration on the [Onager](https://github.com/Feudal-Project/Onager) module will awaken the system and let the magic happen!

### What exactly can be connected to the Trebuchet?
The following appliances can (usually) be controlled via relays and therefore get connected to the Trebuchet:

- Basic lights.
- Blinds/covers with separate control wires for up/down (most of them do). If you are unsure, ask a question in the [Q&A discussion section](https://github.com/Feudal-Project/Trebuchet/discussions/categories/q-a), or consult your local electrician.
- Garage doors which are capable of being wired to a wall switch.
- Any type of binary valve, like infloor heating valves.
-  Many more ESPHome components which use a binary output at the core.

The following devices can be sensed by the Trebuchet:
- Static and momentary wall switches.
- Any type of binary window sensor (switch-based, reed contact).
- Basic motion sensors (PIRs) outputting a binary value.
- Floating switches for water level measurement.
- Many more ESPHome components which use a binary input at the core.

You found another use for the Trebuchet? Awesome! Share it in the [ideas discussion section](https://github.com/Feudal-Project/Trebuchet/discussions/categories/ideas) so others can benefit from your discovery!

### What is possible with the Trebuchet at the base of my ESPHome setup?
The possibilities of using the Trebuchet are close to limitless, due to the sheer number of ESPHome components relying on basic binary inputs and outputs. Nonetheless here are a few examples of typical use cases:

- Using double press on your blind switch, to lower them all the way and tilt them to 50%
- Using long press on a light switch to apply a specific scene, which lowers the blinds, sets the lights to 30% and turns on the TV
- Using a window sensor to automatically turn off the valve for the heating in that room
- Using a PIR to turn on the light if someone is home or send a Home Assistant notification if no one should be home.
- Using five quick presses to activate the house alarm on any light switch all over the home
- Turn down the blinds if a window is left open for an extended period of time.

### Why should I use the Trebuchet instead of other solutions?
If the points listed in “Who is this module for?” are more a nice to have than a must for you, this module is probably not for you. Nonetheless, here are a few reasons why I think you should still consider this system over others available on the market:

- It allows you to strip out the whole system and use your home without any smartness, if you keep a few important points in mind (see [Component section](#component-selection) for more information).
- Very few other systems can be setup so cheaply (see the [Cost section](#cost) for more information).
- Many systems rely on some sort of network connection between them. This system can handle a decently sized flat or even a small home all on one controller. A system more centralized than this is hard to find!
- Define everything yourself! You are a quick with your Fingers? Just set the double press timeout to 20ms, and no one can trigger the scene except you! You are not as fit as you might once were? Set the triple press on any wall switch to send an emergency message to someone over Home Assistant or else. The possibilities are endless, and no company can tell you what to do next, it’s all up to you!
- Modularity at its best! You hate to throw away working tech, even if only one aspect does not work any longer? Just replace it, or even better: get your soldering iron out and repair it yourself using the schematics and information provided here!

### Why are there no Gerber files or project file?
This question is absolutely valid and should not be dismissed or ignored! I created this module after spending many hours of my personal time, both while studying at university and later working a full-time job. Therefore, I personally believe it is fair to make the module available only through a PCB manufacturer that credits my work with a small percentage of the revenue (with no extra cost to you). This way, you can order your PCBs (and even select a few parameters, such as color, etc.) from a well-known manufacturer, while I receive a small commission for my design work. If you still need the production files, however, I believe you're capable of designing your own PCB.

## Wiring
In the light installation schematic below, the typical wiring of a normal wall switch, and the light itself is shown. Commercial systems you typically get on the market do not split the system into distinct parts, as I did for the feudal project. A shelly device for example usually concludes powersupply, controller, relay driver and the relay itself into one device. The all in one approach will result in a smaller footprint inside the cabinet, but will be less repairable. To know more about the “why” and “how” look at [this](#Why-should-I-use-the-Trebuchet-instead-of-other-solutions?) question.

Most of the setup uses 24V as a supply voltage, which makes it safer for humans. Most countries recognize this safety advantage and therefore do not regulate this type of wiring as much as typical household voltage (230V/110V). Therefore, it most likely is allowed for you to work with this voltage at home while not breaking any code or insurance terms (Disclaimer: I do not know your specific situation and I also won’t defend you in any way, if you break your local rules. Do your own research or consult a local electrician!).

The benefit this will give you is to be able to set up the whole system yourself and repair it yourself. The only parts which need to be worked by an electrician is wiring the 230V/110V devices towards the respective relay.

You may ask yourself what benefit this really provides you. Simple answer: Your typical electrician will most likely not be willing to install your favorite smart home system (like shellies or so on). Most often, you need to get in contact with an electrician which has also some sort of IT knowledge and knows your system of choice while also being willing to take the accountability of the installation. With the feudal project, the work for the electrician is simplified to a degree any electrician can handle, and you yourself are able to setup everything the way you want it to.

<p align="center">
  <img src="/images/Treb-Onager-simple-schematic.png" width="80%">
  <img src="/images/Treb-Onager-simple-schematic-cover.png" width="80%">
</p>

## Component selection

### Relay
Most simple appliances can be controlled via a relay. In order to find the best relay for your usecase, a few things need to be considered.

First of all (and most importantly), the relay needs to work with your low voltage level. At the moment the only voltage level for the trebuchet is 24V DC, so make sure, your relay works with this voltage level at the input ports. 

Another important metric is the current rating of the relay. If you power a simple light fixture, a relay capable of 4 or 8A might be enough. If you wish to control an electric heater, you will most likely need a relay able to supply 16A. All in all, you need to make sure to use a correctly rated relay for your usecase. If you are unsure, ask a question in [Q&A discussion section] (https://github.com/Feudal-Project/Trebuchet/discussions/categories/q-a) or consult a local electrician for help.

To minimize your own electric bill, you might want to take a look at the electric consumption of the relay itself. Most of the time, the wattage needed by the relay is stated in the datasheet, but more often than not, this value is a bit higher then what it actually needs. If you want to minimize your consumption, you have to order the relay and measure it yourself with a multimeter. You can also take a look at the comparison table in the 
section. Another option to minimize the relays power consumption can be to use impulse controlled relays. These can be more expensive money wise as well as memory wise. But then ESPHome has to keep track of the current state of the relays, because there is no way for the Trebuchet to know, if the relay is on, or off.

### Power supply
Your power supply selection is mainly influenced by the number of relays and the power needed by the relay itself. The voltage needs to be 24V DC, as no other voltage is supported by the trebuchet at the moment.

I would suggest you choose a power supply from a reputable brand (like Meanwell), because going cheap on this one, will lead to unstable states. In my opinion 20-40€ more on a power supply which most likely will last for 10 years or more are reasonable, compared to a cheap one, which my start to produce coil noises and goes dead in 2-3 years.

**Formular to calculate power supply wattage:**
`Wattage = Number of Trebuchets * 16 * (wattage of relays + 0,084W) + 10W`

With the formular above, you will get a number which should work for your setup in the worst case (all outputs are on, and all switches are closed). This use case is more than unlikely, but you can be sure it’ll work!

If the wattage is above any power supply which you can get a hold of, simply split the power line. Use a power supply for only one or two trebuchets and connect their grounds together. This is possible, because the input and output circuitry is galvanically isolated from the driving logic. If you are unsure, just ask a question in [Q&A discussion section](https://github.com/Feudal-Project/Trebuchet/discussions/categories/q-a).

### Wall switches
You can choose between two types of switches typically. The first option (which is used most often), is the toggle switch. It can get turned on or off, which causes to change the permanent state inside of ESPHome. The momentary switch will flick back into its position as soon as the user releases the switch. As a result, ESPHome will see a short pulse at the input signal.

The answer to which is right for you is simple. If you want to be able to rip out the Smart System and use only the switches and relays later, you should use toggle switches, so that the relays stay on and if the switch is “turned on”. If you want to get the most out of the multiclick feature and hate the fact that a toggle switch might not represent the actual state of the output, you should get momentary switches. Even if you choose momentary switches and want to rip out the feudal project later on, you could just buy toggle switches (to replace the momentary ones), or impuls relays (to replace the normal relays).

## ESPHome configuration
The Trebuchet can be included into ESPHome as a package (a simple copy paste example can be found here). With ESPHome being not able to use external packages as a template at the moment, you need to download the files located [here](https://github.com/Feudal-Project/Trebuchet/tree/main/esphome/packages) and copy them in your ESPHome directory. An explanation on where your ESPHome directory is, can be found [here](https://esphome.io/guides/getting_started_hassio.html#device-builder-interface). To know more about ESPHome packages look [here](https://esphome.io/components/packages.html#packages-as-templates) for official information. An external ESP32 based controller is necessary, as the Trebuchet does not include one by itself. Take a look at the [Onager](https://github.com/Feudal-Project/Onager) as the recommended option, but any ESP32 microcontroller should work as long as its voltage converter is able to provide enough power. The package allows you to configure each input/output with the following parameters:

- ***Module_Name:***
Name your module to your liking.

- ***Module_I2C_Address_input:***
This parameter is the I2C address of the input side of the module. Valid values are between *0x20* and *0x27*. The address must be unique over the whole ESPHome configuration and can be set on the module at the side via the dip switches. A picture explaining how to set the address can be found below.

- ***Module_I2C_Address_output:***
This parameter is the I2C address of the output side of the module. Valid values are between *0x20* and *0x27*. The address must be unique over the whole ESPHome configuration and can be set on the module at the side via the dip switches. A picture explaining how to set the address can be found below.

- ***Outx:***
This parameter sets a part of the name and ID of the respective output (*Out0*-*Out15*). The name and ID of the output is a combination of *Module_Name* and *Outx* value separated with “_”. If you wish to reference the Output in a script, or automation reference it by its ID (<*Module_Name*>\_<*Outx*>)

- ***Outx_restore_mode:***
Set the restore mode of the output to a desired value. Look at the [official ESPHome configuration](https://esphome.io/components/switch/index.html#base-switch-configuration) for more details.

- ***Outx_interlock:***
Set the interlock parameter of the output to a desired value. Look at the [official ESPHome configuration](https://esphome.io/components/switch/gpio.html#interlocking) for more details.

- ***Outx_internal:***
Set the internal boolean of the output to a desired value. Look at the [official ESPHome configuration](https://esphome.io/components/switch/index.html#base-switch-configuration) for more details.

- ***Inx:***
This parameter sets a part of the name and ID of the respective input (*In0*-*In15*). The name and ID of the input is a combination of *Module_Name* and *Inx* value separated with “_”. If you wish to reference the input in a script, or automation reference it by its ID (<*Module_Name*>\_< *Inx* >)

- ***Inx_internal:***
Set the internal boolean of the input to a desired value. Look at the [official ESPHome configuration](https://esphome.io/components/binary_sensor/#base-binary-sensor-configuration) for more details.

<p align="center">
  <img src="/images/Treb_cut_marked.jpg" width="80%">
</p>

The packages uses scripts, which get called if a specific event is triggered. Using this method, I was able to extract all the config code for a trebuchet, while also using the automation feature of ESPHome. At a first glance, the scripts might overcomplicate the configuration, but they allow to organize the configuration into different files and allow reuse. Examples of typical configurations can be found here.

Using the multiclick feature of ESPHome, it is possible to create your own click patterns. As a basis the Trebuchet uses a simple package introducing single, double and long press click patterns. If you are missing features, you can always create your own. Keep in mind, that the configuration provided is a compromise between easy of use and customizability.

- ***Inx_script_singlepress:***
Set the script ID which should be called if a “singlepress” is recognized by the multiclick feature. Information about scripts can be found [here](https://esphome.io/components/script.html), while information about the multiclick feature can be found [here](https://esphome.io/components/binary_sensor/index.html#on-multi-click).

- ***Inx_script_doublepress:***
Set the script ID which should be called if a “doublepress” is recognized by the multiclick feature. Information about scripts can be found [here](https://esphome.io/components/script.html), while information about the multiclick feature can be found [here](https://esphome.io/components/binary_sensor/index.html#on-multi-click).

- ***Inx_script_longpress:***
Set the script ID which should be called if a “longpress” is recognized by the multiclick feature. Information about scripts can be found [here](https://esphome.io/components/script.html), while information about the multiclick feature can be found [here](https://esphome.io/components/binary_sensor/index.html#on-multi-click).

- ***Inx_on_press:***
Set the script ID which should be called if an “on press” is event is called by ESPHome. Information Information about scripts can be found [here](https://esphome.io/components/script.html), while information about the multiclick feature can be found [here](https://esphome.io/components/binary_sensor/index.html#on-multi-click).

- ***Inx_on_release:***
Set the script ID which should be called if an “on release” is event is called by ESPHome. Information about scripts can be found [here](https://esphome.io/components/script.html), while information about the multiclick feature can be found [here](https://esphome.io/components/binary_sensor/index.html#on-multi-click).

## Cost
The cost of implementing the feudal project will be highly unique to your home, because the wiring cost will be by far the highest expense! Therefore you should consult an electrician for pricing on that topic, if you are not doing it on your own.

Concerning the cost of the modules and the needed additional hardware, a rough estimation is below (prices were looked up in January of 2025)

#### Component Price (excluding shipping)
- 150W Meanwell Power supply (for 1 [Onager](https://github.com/Feudal-Project/Onager), 4 Trebuchets and many relays): ~40€
- One Trebuchet modul including all the necessary components (excluding the casing):  ~15-20€ **will be updated soon!** (depending on the number of modules you order)
- Trebuchet casing printed at home: ~5€
- One Relay (16A, 24V): ~10€
- One [Onager](https://github.com/Feudal-Project/Onager): **will be updated soon!**
- Wall switches: entirely up to you!

#### Setup Price (excluding shipping)
A small setup (64 Inputs, 64 Outputs) would cost somewhere around 700-800€, without the wall switches and excluding shipping and wiring costs. As an example, 16 Shelly Pro 4PM (comparable in terms of IO, but having additional power measurement) would land you around 1.800€. If you don’t need power measurement and want to create your own system on a budget, the Feudal project is a valid alternative.
