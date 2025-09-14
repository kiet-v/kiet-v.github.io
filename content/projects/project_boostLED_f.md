---
author: "Kiet Vu"
title: "Dimmable Blue LED from AA battery"
date: "2021-05-17"
description: "Driving blue LED from a 1.5V AA battery"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
weight: 2
---
This is a small project where I want to power a blue LED (which has Vf~ 3V @ 10mA) with a 1.5V AA Battery by building a boost converter using discrete components. 

LED represents a constant voltage load, so this is slightly different scenario where you don't directly control output voltage. This boost converter operates in DCM, and acts somewhat like a current source. The LED brightness is controlled by the duty cycle of the boost converter - it does not control the load voltage, but instead control the inductor "charging time", which is related to average current per cycle being delivered to the load. Switching waveform and its duty cycle control are created by schmitt trigger(s) and potentiometer circuits. 

<iframe width="800" height="450" src="https://www.youtube.com/embed/rUXpJMiEA4A?si=KeSIjDj2aHER05F1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>







