---
author: "Kiet Vu"
title: "DDR Pad"
date: "2025-05-26"
description: "Making a light-weight DDR Pad"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
weight: 3
---

One of my favorite rhythm games is DDR/ITG - it's quite hard to beat a combo of good soundtracks, engaging gameplay, and actually getting some considerable workout. At the time, MIT machine (yes MIT does have a DDR machine, and yes it is amazing) unfortunately broke down, so that leaves me on a DDR drought. So gives me an excuse to try to build my own DDR pad... My plan is to build a DDR pad that is quick to put together, and convenient to use.  

The plan is as follow: 
- Have a piece of plywood as a base, and band-saw individual step panel using another piece of plywood. 
- Put a 'soft' material and sensor between the step panel and base
- Do some wiring, soldering, coding
- Profit (?)   

I went to Home Depot to get myself some plywoods and cut them into a base and step panels (the base end up being 2.5' x 2.5'). I also got my hands on the following force sensors [Interlink Force Sensor](https://buyinterlinkelectronics.com/collections/x-ux-force-sensors/products/fsr-ux-408-200mm-length), which can be cut to length. I find them to be quite nice to use. 

For microcontroller, I use the Teensy 4.0, which is what I have on hand and also suitable for what I need. It has enough onboard ADCs and Teensy also has HID library that I can use to configure my pad into a keyboard. The pad does have some "debounce" behavior - the step panel usually takes around 20ms after being stepped on to recover - which means I do have to set ~25 ms of debounce time for my pad. My step speed limit is definitely way lower than 40 steps a second... so this should be adequate.   

I would say I find the pad to be adequate for what I need! One bonus of this pad design I can carry them around. Also since I use velcro, I can remove the step panel quickly. Using analog sensor also allows me to adjust sensitivity level of the pad, which makes it quite responsive. Of course arcade spec pad, but this

Though the hardest part, it turns out, is finding a place to use it without being obnoxiously loud.