---
layout: post
title:  "BMES Make-A-Thon: Gait Monitor"
categories: Projects On-going
---

> An open-source gait monitoring solution as a collaboration between the Biomedical Engineering Society @ UCI and the Children's Hospital of Orange County

In order to expand my engineering breadth further than my major field of story, I joined the Biomedical Engineering Society and closely worked with them to design an open source gait monitoring solution.

<!--more-->

For the first Biomedical Engineering Society @ UCI (BMES) Make-A-Thon, we were given seven weeks to identify a problem in the transition from pediatric to adult care for the Children's Hospital of Orange County.

## BMES Team

- Matthew Lo
  - Clinical Needs and Solution Identification
- Christine Ly
  - 
- Derek Nutz
  - Case Engineer
- Adrian Ornelas
  - Embedded Systems Engineer
- Vietbao Tran
  - Web App Development

## Problem Definition

Within the medical industry, a great deal of fragmentation exists between the different aspects of health care. For example, it is often difficult to review a patients medical history once they change primary healthcare providers. Today, the medical industry seeks to remedy this problem with the introduction of EHR's, Electronic Health Records. 

In order to ease the transition from pediatric care to adult care for children, we intend to create an open source standard for gait monitoring data that can be easily saved and opened in the industry standard EHR software that medical staff are already familiar with using.

Additionally, we hope to bring to market a cost effective and open source gait monitor that is able to utilize the new open standard that we are creating in order to reinforce physical therapies in patients and accelerate their recovery after suffering from a motor impeding neurodegenerative disorder. Our designs are going to be open source and freely available to the public in order to increase both medical transparency and enable a lower cost to entry for gait monitoring in a clinical setting.

## Design Overview

Our first prototype of a gait monitor was built using a number of technologies and existing embedded system solutions. Our solution involves two assemblies, one for each leg. Each assembly consists of two main parts, the base which is mounted at the knees, and a retractable supplementary accelerometer which clips onto the patient's footwear. Each gait monitor is equipped with an ESP-32, 1000 mAh rechargeable battery, and two accelerometers.

My role on the team has been to design the firmware that records and sends the data from the accelerometer to the end user on the web app. 

In order to do this I utilized the i2c communication protocol in order to interface with the MPU 6050 accelerometers. In order to transfer the data to a patient's or doctor's device, I utilized the Bluetooth Low Energy Mesh network in order to stream the patient's data securely and wirelessly.

{% include image.html image="BMES/GATT-BLE-ESP32.png" alt_text="BLE Protocol Diagram" height="15rem" %}

Bluetooth Low Energy, often abbreviated as BLE, is a communication protocol that relies on the abstraction of services to function in a dynamically adjusting mesh network to transfer information. In order to make our medical device compliant, we defined our BLE Service and Characteristics along the BLE standards for auxillary medical monitors. We then used this BLE characteristic in order to securely push the patient's accelerometer data to the web app.

On the web app, we parse the stream of bytes into a human readable format in the form of various acceleration and position charts. In the future as we move forward with our collaboration with the Children's Hospital of Orange County, we hope to create an inverse kinematic rigged model in order to further illustrate a patient's individual gait patterns in an easy to understand way.

For further information on the design of the device our presentation is avaiable below:

{% include pdf.html pdf="BMES/Make-A-Thon_Presentation.pdf" height ="500em" %}