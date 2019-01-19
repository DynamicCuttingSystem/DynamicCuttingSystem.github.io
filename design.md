---
layout: page
title: Design
description: "Design Overview"
---

# Mechanical Overview
<div style="text-align:center"><img src="/img/mechoverview.png" /></div>
<div style="text-align: justify">The mechanical design consistes of a conveyor that leads into a guiding tray. A camera above the conveyor detects the type of vegetable. Vegetables that pass the guiding tray are directed into a holding container. Once a vegetable is in here, the conveyor stops so the vegetable can be cut before any additional vegetables are moved into the guiding tray.</div>
<div style="text-align:center"><img src="/img/detailview1.png" width="600" /></div>
<div style="text-align: justify">Once the vegetable is in the holding container, a linear actuator pushes against the vegetable to hold it tightly vertically. Then, a blade connected to a scotch yoke mechanism cuts a slice at the bottom. The cut slice is pushed out with the push bit below the blade. Then the linear actuator is relaxed so the vegetable can move down slightly and the process is repeated.</div>
<div style="text-align:center"><img src="/img/detailview2.png" width="600" /></div>
<div style="text-align: justify">The turntable that collects the vegetable slices is rotated to match the appropriate bin as that of the detected vegetable.</div>

# Electrical Overview
<p><div style="text-align: justify">Three motors and a linear actuator are used in this design. As the control of these motors needs to be deterministic and time sensitive, a controller with a real time operating system (RTOS) and/or low interrupt latency is required. However, since this logic is very simple, a high-speed controller is not required. An Arduino (which has a speed of 16 MHz) is sufficient for these specs. Therefore, an Arduino Uno is selected for this project as it is the most cost-effective solution for a low number of input/output (IO) pins for connections.</div></p>
<p><div style="text-align: justify">The Arduino is good for deterministic real-time logic, but when it comes to image processing and computer vision, it is advantageous to use a general-purpose operating system as the operations tend to be computationally heavy and general-purpose operating systems are better suited to handle them, especially with the variety of libraries and frameworks widely available for them. Therefore, a Raspberry Pi is chosen because it is compact, it can run embedded Linux (which comes with all the benefits that Linux provides such as in-built network related drivers), and it also has wireless capabilities.</div></p>
<p><div style="text-align: justify">To capture images of the vegetable on the conveyor, The Camera Module V2 for the Raspberry Pi is chosen as it is cheap and comes with native library support, thus allowing for rapid prototyping. For feedback purposes, it is required to know when a vegetable is in the holding container. The easiest way to achieve this is using a pressure sensor on the vegetable support base. Therefore, a simple force sensitive resistor (FSR) – the Interlink 402 – is selected for this purpose. The final block diagram summarizing the electrical assembly overview is shown below.</div></p>
<div style="text-align:center"><img src="/img/elecoverview.png" /></div>
<div style="text-align: justify">See the <a href="/prototype/">Prototype</a> page for the prototype development.</div>