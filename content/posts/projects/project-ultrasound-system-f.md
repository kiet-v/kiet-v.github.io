---
author: "Kiet Vu"
title: "★ Tabletop Ultrasound Imaging System"
date: "2026-09-24"
description: "MIT MechE Master Thesis"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["/ultrasound/", "/posts/projects/project-adc-highspeed-f/", "/posts/projects/project-uls-transceiver-board-f/", "/posts/projects/project-uls-pulser-board-f/"]
ShowToc: true
TocOpen: true
weight: 1
---

## Power Board

The power board is designed to power the transceiver board, which requires several different voltage levels. These include the following:

| Rail | Topology | Usage |
|---|---|---|
| ±85 V (adjustable, isolated) | Isolated flyback converter | The pulser's high-voltage supply, which fires the transducers |
| +15 V / −15 V | Buck and inverting buck converters | The time-gain compensation (TGC) circuit, regulated down to ±13 V for its op-amps |
| +6 V | Buck converter | Input to the transceiver's low-noise regulators, which make the front-end, pulser-logic, clock and Teensy rails |
| −8.6 V | Dual-polarity charge pump | Input to the −5 V regulator for the pulser's negative low-voltage rail |

Everything comes from one 24 V input with a protection circuit, and the flyback stays off by default until its enable jumper is set.

<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/photo.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/photo.webp" alt="Ultrasound power board" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>


### Layout
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/3d.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/3d.webp" alt="Power board, 3D view" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Power board, 3D view</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/overview.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/overview.webp" alt="Power board, all layers" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Power board, all layers</div></div>
<details>
<summary style="cursor:pointer;font-weight:600;margin:8px 0">Show all 4 layers</summary>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/layer1-sig.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/layer1-sig.webp" alt="Layer 1 · SIG (top)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 1 · SIG (top)</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/layer2-gnd.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/layer2-gnd.webp" alt="Layer 2 · GND" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 2 · GND</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/layer3-pwr.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/layer3-pwr.webp" alt="Layer 3 · PWR" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 3 · PWR</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/pwr/layer4-sig-gnd.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/pwr/layer4-sig-gnd.webp" alt="Layer 4 · SIG/GND (bottom)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 4 · SIG/GND (bottom)</div></div>
</details>

### Schematic
<embed src="/images/ultrasound/pwr/schematic.pdf" type="application/pdf" width="100%" height="600px" />

[Open the schematic as a PDF](/images/ultrasound/pwr/schematic.pdf)

## Transceiver Board (WIP)

### Layout
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/overview.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/overview.webp" alt="Transceiver board, all layers" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Transceiver board, all layers</div></div>
<details>
<summary style="cursor:pointer;font-weight:600;margin:8px 0">Show all 6 layers</summary>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer1-sig-top.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer1-sig-top.webp" alt="Layer 1 · SIG_TOP (top)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 1 · SIG_TOP (top)</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer2-gnd-top.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer2-gnd-top.webp" alt="Layer 2 · GND_TOP" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 2 · GND_TOP</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer3-sig-analog.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer3-sig-analog.webp" alt="Layer 3 · SIG_ANALOG" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 3 · SIG_ANALOG</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer4-pwr.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer4-pwr.webp" alt="Layer 4 · PWR" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 4 · PWR</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer5-gnd-bottom.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer5-gnd-bottom.webp" alt="Layer 5 · GND_BOTTOM" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 5 · GND_BOTTOM</div></div>
<div style="margin:18px 0;text-align:center"><a href="/images/ultrasound/xcvr/layer6-sig-bottom.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/ultrasound/xcvr/layer6-sig-bottom.webp" alt="Layer 6 · SIG_BOTTOM (bottom)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a><div style="font-size:0.9em;opacity:0.75;margin-top:4px">Layer 6 · SIG_BOTTOM (bottom)</div></div>
</details>

## High Speed ADC Board Prototype

<img src="/images/adc/3Dview.png" alt="ADC board 3D view" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
(More Views, Schematics and Layouts in later sections)

### Goal
* As a part of my research, I'm currently building an ultrasound kit, which includes subsystems like receiver, pulser and power supply. A part of the challenge is to process the stream of data coming from the receiver using FPGA, and for that I need something that can simulate receiver data since my system is still in development. I decide to build a standalone ADC board that can output LVDS data similar to what ultrasound receiver usually outputs. This specific board would interact with Alchitry Au V2 FPGA board.

* This would be useful board that allows me to simutaneously do development with the FPGA, while I'm rooting out the circuit design for other parts of the ultrasound system. This is also a good practice on laying out high-speed PCB board for me. By itself, it would also be a nice board for general measurement (and one step closer to building my own oscilloscope)! This is a first version of the board, and my plan is to gradually improve it over time.

### IC Selection
* I decided to use the AD9219 from ADI, which is a 65 MHz, 10 bits ADC. Its sampling rates, resolution and LVDS outputs are similar to what I need. Another reason is this IC is a part of a family of IC (AD9228...) that is pin-compatible. This board is built with such upgrade in mind - I should only need to replace the clock and the ADC with its pin compatible version. This IC also has an optional SPI line that allows me to program the IC with FPGA, but still works if I don't use it (which is a nice risk reduction)
* The LVDS outputs are shown below. There's a PLL inside the IC that takes in the input clock (CLK) and generate output clock (FCO) that scales by number of resolution bits (meaning if I have 40 MHz clock, I will get 40 x 10 MHz since my IC is 10 bits). Output data line is sampled on both rising and falling edge of the output clock signal.
<img src="/images/adc/lvdsprotocol.png" alt="AD9219 LVDS output timing" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">

### Front-End and ADC Driver
* I currently have two (out of four) input channels using the ADA4932 ADC driver, which has a -3dB bandwidth of up to 560 MHz. This helps me with noise immunity and also allow me to adjust the gain of the signal. I was planning to use RF transformer, but since my application is broadband, I decide to go with this route instead. If this works well, I will have all the channels 'upgraded' to be using this IC.

* In future iterations, I will also try to redesign the front-end so that it can take higher input voltage.

### Clock Selection
- High speed ADC System requires a clean clock signal. The requirement becomes more stringent as you go to higher sampling frequency and resolution (see AN-501 application notes from ADI, the image below is taken from Figure 5):
<img src="/images/adc/SNRjitter.png" alt="SNR versus clock jitter" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
- I select a clock (LMK6C from TI) which has 500fs maximum RMS jitter at 100MHz (12kHz to 20MHz integration BW).
- RF Transformer is used to convert single ended clock signal to differential, with a pair of high speed schottsky diode being placed to limit input voltage.

### Layout Notes
* I use the following stack up: SIG1 - GND - PWR - SIG 2 (with ground pour).
    * High speed traces are on the top layer
    * Solid ground plane on second layer
    * Lower speed traces are on the bottom layer
* The component placement is such that each distinct group of high-speed signal (input and ADC driver signals, clock, LVDS lines) does not overlap with each other and is sufficiently spaced apart
* 100 Ohm Impedance Control for LVDS lines on top layer
    * I use the JLC04161H-7628 Stackup since it's the cheapest
    * Interpair and Intrapair lengths are matched to reduce skew
    * Solid, continuous ground underneath these high-speed traces
    * Keep these traces shorts and 'distanced' away from other traces.
* Clock trace is kept short and close to the IC
* FPGA placement is very close to minimize the length of LVDS signals

### Views and Layers
<img src="/images/adc/2Dview.png" alt="ADC board 2D view" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
<img src="/images/adc/3Dview.png" alt="ADC board 3D view" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
<img src="/images/adc/sig1.png" alt="Layer 1 (SIG1)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
<img src="/images/adc/gnd.png" alt="Layer 2 (GND)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
<img src="/images/adc/pwr.png" alt="Layer 3 (PWR)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">
<img src="/images/adc/sig2.png" alt="Layer 4 (SIG2)" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px;margin:18px auto">

### Schematics and Stackup
- Schematic:
<embed src="/images/adc/ADC_LVDS_Testboard.pdf" type="application/pdf" width="100%" height="600px" />
[Open the schematic as a PDF](/images/adc/ADC_LVDS_Testboard.pdf)
<br></br>
- Stack up:
<embed src="/images/adc/Stackup.pdf" type="application/pdf" width="100%" height="600px" />
[Open the stackup as a PDF](/images/adc/Stackup.pdf)

### Test Video
<video controls preload="metadata" playsinline poster="/images/adc/lvds-test-poster.webp" style="display:block;width:100%;max-height:520px;margin:18px auto;border-radius:4px;background:#000">
<source src="/images/adc/lvds-test.mp4" type="video/mp4">
</video>

[Watch on Dropbox](https://www.dropbox.com/scl/fi/fjdu3rmxurewdxy5aceu5/Video-Jul-23-2026-12-34-06-AM.mov?rlkey=5jkli7kg0wu43yiqrunddgyd3&dl=0)
