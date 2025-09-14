---
author: "Kiet Vu"
title: "★ Op-amp based line following robot"
date: "2021-06-02"
description: "'What if we are not using a microcontroller?'"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
weight: 5
---

Every semester, MIT 2.678 (Electronics for Mechanical System I, and a class in which I was being a learning assitant) holds a competition every year where students built line-following robot that traverses a pre-defined course. During our lab session, there's a discussion with Steve Banzaert (the technical instructor of the course) and my fellow LAs/TAs : what if we don't have a microcontroller? That conversation then subsequently leads to the creation of this project. I built this robot over the course of 2-3 weeks, during the time of the competition. 

Here's the robot in all its glory: 
![Problem Description](/images/linefolowerrobot/line-following.png)

This robot takes in each reflectance sensor's analog data (the competition is limited to 3 sensors), goes through a bunch of op amps that implements mathematical operations and feedback controller, and drive the H bridges that control the motors. 
# Video Demo
<iframe width="800" height="450" src="https://www.youtube.com/embed/Lg4wDQBDzK8?si=LXDJDuG85EHqN1Oc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Maybe one day I will implement state control to deal with custom scenarios presented by the board (or not...)

