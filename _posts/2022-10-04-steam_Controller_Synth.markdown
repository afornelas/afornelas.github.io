---
layout: post
title:  "Steam Controller Synth"
category: Engineering
---

>Turning Valve's Steam Controller into a fully functional Synth, compatible with MIDI files and input devices with full polyphony

Continuing off of [Pila's](https://gitlab.com/Pilatomic/SteamControllerSinger) work, steamControllerSynth expands and enables the playback of MIDI data from both MIDI files and live playback from input devices. Instead of being limited to one voice per channel, and two total channels, this script implements a dynamically allocating queue in order to fully saturate all haptic motors connected to the computer enabling full polyphony for every MIDI channel, limited only by the amount of Steam Controllers avaiable.

<!--more-->

## Steam Controller Background

Valve's Steam Controller is a video game controller that was originally released in November 2015 in order to bridge the gap between games that utilized traditional controllers and keyboard and mouse such that they would be more accessible to all. In order to emulate a mouse pad on a controller footprint, Valve included two haptic touchpads each equipped with linear resonant actuators. From Steam's original page for the Steam Controller:

> These small, strong weighted electro-magnets are attached to each of the dual trackpads. They are capable of delivering a wide range of force and vibration, allowing precise control over frequency, amplitude, and direction of movement.

By leveraging the precise control of the actuators made available through the hardware, we are able to modulate the frequency at which the linear resonant actuators are oscillating to an incredibly high degree. Through this we can oscillate the trackpads according to the frequencies that correspond to musical notes.

This has already been done by two teams. The first team is Valve themselves, they utilized their accuracy in order to enable power on and off tunes when using the computer. Secondly, [Pilatomic](https://gitlab.com/Pilatomic/SteamControllerSinger) has created a similar program to reproduce midi files through the Steam Controller's haptic motors.

The implementation that I have created differs from the former projects in two key areas. Both Valve and Pila did not allow for multiple steam controller to play in sync, effectively limiting them to two tone polyphony. Instead, I wanted to create a method of incorporating several different Steam Controllers in unison to significantly increase the polyphony and quality of music reproduction. Additionally, neither of the previous solutions were able to parse MIDI data in real time and change the Steam Controllers into a live Synthesizer.

My take on the software, Steam Controller Synth, addresses these two key areas and finally enables the ability to both fully resolve orchestrated midi files completely and playback MIDI inputs in real time. 

More information on how to use the software is available here:
on the [Github Page](https://github.com/afornelas/steamControllerSynth)

## Examples

<!-- Play some cute (royalty free) music here and attach an MP3 player and a video or two. -->

Pending a visit to a recording studio, stay tuned (haha get it)