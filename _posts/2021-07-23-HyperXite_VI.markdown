---
layout: post
title:  "HyperXite VI"
---

# HyperXite VI

![HyperXite Logo](/assets/HyperXite/hx_eng_logo.png)

> [Hyperxite.com](https://www.hyperxite.com/) - Innovating the future of travel, one prototype at a time

Throughout the 2020-2021 academic school year, I served on HyperXite VI's controls subsystem as an Embedded Systems Engineer to compete at the [European Hyperloop Week International Design Competition](https://hyperloopweek.com/).


## Design Overview

The control subsystem's purpose is to build and test the embedded system comprising of Micro Controller Units (MCU’s) and various peripherals that include Pressure Transducers, Voltage and Current Sensors, Electronic Speed Controller, Base Station, Battery Management System (BMS), and Inertial Measurement Unit (IMU). The pod operates on a Finite State Machine (FSM), and the MCU will use signals from its peripherals to drive the pod by evaluating each state in the FSM and transitioning to the appropriate state. In addition to building the system for pod operation, we also implemented our own communication protocol that operates between two [Ubiquiti M900 Rocket Radios](https://www.ui.com/airmax/rocketm/). 

Our design consists of a host computer to interface with the pod, and two microcontrollers operating in tandem to collect, compile, and analyze data in real time in order to ensure safe operation of the pod. For the host computer, our code is written to be platform agnostic and will run on any major supported Operating system with little modification. This GUI-enabled program is written largely in Python 3 and the PyQt GUI library. Through the tools provided in PyQt we created a communication protocol that polls the hyperloop pod at a rate between 10 and 50 hz. 

![HyperXite Gui](/assets/HyperXite/hx_gui.png)

For the target microcontroller, the Raspberry Pi 4, our code is platform specific towards the Debian based linux distribution Raspberry Pi OS, and written largely in Python 3. This code is primarily designed to be modular, and easy to implement or remove in order to rapidly adjust to the changing needs of the HyperXite VI Pod. As such every component that we read from is written in its own python module in order to greatly simplify the main loop of the program and to facilitate debugging and changing of sensors and components.

Lastly, our third device, the ESP 32, makes up for the weak points of having a Raspberry Pi 4 as our main microcontroller. While the Raspberry Pi 4 features high speed performance, it lacks the ability to perform real time tasks and read analog voltages from GPIO. The ESP 32 is currently using full duplex SPI to stream information to the Raspberry Pi in real time. 

![Finite State Machine](/assets/HyperXite/FSM.png)

This finite state machine dictates all of the valid states of the pod and how it transitions between all of them. This was designed in order to ensure the safe operation of the pod at all times.

## CAMP Statewide Undergraduate Research Symposium @ University of California

In addition to presenting to the European Hyperloop Week 2021 Competition in Valencia, Spain, I also presented to the California Alliance for Minority Participation 2021 Statewide Research Symposium  on Friday, February 12, 2021. Attached below are the presentation, awards ceremony (awarded at 8:20), and a picture of the plaque.

{% include youtube_embed.html id="rgcKyu4Nejg" %}

{% include youtube_embed.html id="V2nPEFiNWLI" %}

![CAMP Award Plaque](/assets/HyperXite/camp_seal.jpg)