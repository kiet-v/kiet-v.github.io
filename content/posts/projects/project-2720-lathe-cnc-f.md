---
author: "Kiet Vu"
title: "★ Tabletop 2-Axis CNC Lathe"
date: "2026-05-12"
description: "Machine Design (2.720) Group Project"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
ShowToc: true
TocOpen: true
weight: 2
robotsNoIndex: true
sitemap:
  disable: true
---

For MIT 2.720 Machine Design,  I worked with a team of 5 to build a CNC lathe. This page documents my contributions to the overall effort!

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/results/lathe.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/results/lathe.webp" alt="Our tabletop 2-axis CNC lathe" loading="eager" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

## Modelling

### Spindle Thermal Modelling
[2.720 Thermal Modelling](https://docs.google.com/spreadsheets/d/1iBMKO5w6liGEuO9EO1kTqDAOgspm6WDuAE_-bHIFFwc/edit?usp=sharing)
- I went through the process of modelling losses, thermal circuits, and growth modelling (transient and steady state) to predict steady state temperature / growth
- I learned how to model losses in rotating system, taking into consideration of seals, , estimating heat transfer coefficient (h_cond and h_conv), and do a first order modelling of temperature growth over time

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/thermal-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/thermal-1.webp" alt="Spindle thermal model, 1 of 4" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/thermal-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/thermal-2.webp" alt="Spindle thermal model, 2 of 4" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/thermal-3.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/thermal-3.webp" alt="Spindle thermal model, 3 of 4" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/thermal-4.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/thermal-4.webp" alt="Spindle thermal model, 4 of 4" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Spindle System Stiffness Modelling
[[2.720] Spindle Stiffness Matrix Model](https://docs.google.com/spreadsheets/d/1PmyXOsUR7zPWyK-1Z3-MIyldv1UG6LvoIuaFA0WrE20/edit?usp=sharing)
- In order to calculate system stiffnesses, which include bearing shaft geometry, I go with the stiffness matrix method.
- This was useful for obtaining both ‘nominal’ stiffnesses and cross-term stiffness. This also allows me to do sensitivity study for every geometry and bearing stiffness value with a help of app script
- This would be a very useful general calculator going forward for me, as the configuration is ubiquitous. I would say this is one of my favorite works in this class, I really liked how the sheet turns out

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/stiffness-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/stiffness-1.webp" alt="Spindle stiffness matrix model, 1 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/stiffness-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/stiffness-2.webp" alt="Spindle stiffness matrix model, 2 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/stiffness-3.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/stiffness-3.webp" alt="Spindle stiffness matrix model, 3 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Bolted Joint
[[2.720] Bolted Joint Calculator](https://docs.google.com/spreadsheets/d/1kisZyenQnK3MmaJo9v6M7o_yNXr16O4M36CEEVTmM0c/edit?usp=sharing)
- I create a versatile bolted joint calculator that support both blinded joint and clamped members - include joint stiffness, joint strength & separation behavior, and preload settings with friction consideration

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/bolted-joint-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/bolted-joint-1.webp" alt="Bolted joint calculator" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/bolted-joint-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/bolted-joint-2.webp" alt="Preload torque versus preload force, with friction scaling" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Cross Slide Bushing Stack Selection
- I went through the process of selecting bushing configuration for X slide, including friction, lifetime, stiffness, etc.implementing pugh
- Loadpath is analyzed to determine the system stiffness

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/bushing-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/bushing-1.webp" alt="Cross slide bushing stack load path" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/bushing-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/bushing-2.webp" alt="Bushing selection Pugh chart" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Belt Drive Design
[[2.720] Belt Drive Model](https://docs.google.com/spreadsheets/d/1fML9QqgGpfhSYXOj1tK9G8uYHJAXQsFQpf-ya0KSGJw/edit?usp=sharing)
- I designed the drive system, which consider motor dynamics, belt sizing (power and speed rating, strength), as well as setting tension properly

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/belt-drive-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/belt-drive-1.webp" alt="Belt tension and wrap angle calculation" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/belt-drive-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/belt-drive-2.webp" alt="Motor and belt operating-condition table" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Carriage Rail Flexure
[2.720 Carriage Rail Flexure](https://docs.google.com/spreadsheets/d/1wgpvy12Ztqv7EAWJuPQWSU6F6JIkf7HPojaNMNMvEX0/edit?usp=sharing)
- I modelled the stiffness and combined stress on the CRF induced by displacement load (misalignment), shock load and buckling analysis to find the appropriate geometry

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/crf-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/crf-1.webp" alt="Carriage rail flexure stiffness and stress model" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/modelling/crf-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/modelling/crf-2.webp" alt="Carriage rail flexure buckling analysis" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

## FEA

### Spindle Subsystem FEA: Thermal
- I performed thermal FEA (including temperature and elongation) to find shaft temperature and growth

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/spindle-thermal-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/spindle-thermal-1.webp" alt="Spindle thermal FEA, 1 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/spindle-thermal-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/spindle-thermal-2.webp" alt="Spindle thermal FEA, 2 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/spindle-thermal-3.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/spindle-thermal-3.webp" alt="Spindle thermal FEA, 3 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Spindle Subsystem FEA: Statics & Dynamics
- I performed statics FEA under different loading conditions to determine the stiffness values and ensure that our shaft survives under load

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/spindle-static-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/spindle-static-1.webp" alt="Spindle static FEA" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/spindle-modal-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/spindle-modal-1.webp" alt="Spindle frequency study results" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Cross Slide Subsystem FEA
I performed FEA on various parts of the X slide assembly, including:
- Assessment on radial nut thread shear (Delrin vs. Brass).
- Temperature Distribution
- Cross Slide System Stiffness

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/cross-slide-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/cross-slide-1.webp" alt="Cross slide FEA, 1 of 2" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/cross-slide-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/cross-slide-2.webp" alt="Cross slide FEA, 2 of 2" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/cross-slide-thread-shear.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/cross-slide-thread-shear.webp" alt="Nut thread shear FEA" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fea/cross-slide-nut.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fea/cross-slide-nut.webp" alt="Nut adjustability FEA" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

- I learned to perform different types of FEA (thermal, statics, combined thermo-statics and dynamics) and considering different aspects, including: Mesh size and mesh control, setting correct boundary conditions, applying different type of loads (displacement load, force/torque load and remote load) to accurately present the situation, as well as always check your FEA result against ‘reality’. I also assisted my teammate with DQ FEA, and got to experience some flexure FEA action!

## CAD

### Headstock
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/cad/headstock.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/cad/headstock.webp" alt="Headstock CAD" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Carriage Rail Flexure
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/cad/crf.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/cad/crf.webp" alt="Carriage rail flexure CAD" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

- I designed the CRF, informed by modelling to make sure the rail can take up misalignment and shock load , The design also takes into account waterjet taper and manufacturing

### Drive System
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/cad/drive-system.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/cad/drive-system.webp" alt="Drive system CAD" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

- I designed the drive system, including the motor mount, tensioning arm, pulley and belt selection, and idler arm

- I have gotten better at GD&T, as well as general mechanical design ‘sensibilities’ (such as including features that make machining / assembly easier.
- Paying closer attention to tolerance specification, and recognizing important features
- DFM - create parts and include features to make them manufacturable and easily assembled

## Fabrication (Mechanical) & Measurements

### Spindle End Cap
- Waterjet and Mill

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/end-cap.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/end-cap.webp" alt="Machined spindle end caps" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Drive System (all)
- Motor Mount + Shield Mount: Waterjet Mill
- Pulley Hub: Lathe & Mill
- Tensioning Arm: Mill + Tapping Arm

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/drive-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/drive-1.webp" alt="Drive system parts, 1 of 2" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/drive-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/drive-2.webp" alt="Drive system parts, 2 of 2" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/drive-pulley-hub.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/drive-pulley-hub.webp" alt="HTD 5M pulley on the machined hub" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Anti-Backlash Brass Nut (X Slide)
- Mill
- Tapping Arm

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/anti-backlash-nut.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/anti-backlash-nut.webp" alt="Anti-backlash brass nut" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Carriage Side Skirt
- Waterjet
- Mill

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/fab/carriage-skirt.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/fab/carriage-skirt.webp" alt="Carriage side skirt" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Spindle Efficiency Measurement
- Measuring losses generated from the spindle
- [2.720 Spindle Power Loss Characterization](https://docs.google.com/spreadsheets/d/1eDhVTIEeQAsDHcHicdbg_860q7vsfyhGMuFIQPZtHLc/edit?usp=sharing)

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/measure/spindle-loss.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/measure/spindle-loss.webp" alt="Spindle power loss measurements" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Chuck Runout Measurement
- A dowel pin is mounted onto the 4 jaw chuck and dialed in using dial indicator, then chuck is mounted on the pin to measure chuck contribution
- Measurement video: [IMG_6770.MOV](https://drive.google.com/file/d/1yB54oc12JiDN8IhBP4B7iXGCxhtg9Y4I/view?usp=share_link)

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/measure/chuck-runout.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/measure/chuck-runout.webp" alt="Chuck runout measurement setup" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### CNC Stepper Calibration and Measurement
- Leadscrew calibration is required to accurately map the number of command pulses to the actual travel
- [X and Z Calibration](https://docs.google.com/spreadsheets/d/14D-DR9obyx3Pduo02_1g8GyHvB59hoy1FVBRXXwRh_A/edit?usp=sharing)

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/measure/leadscrew-calibration.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/measure/leadscrew-calibration.webp" alt="X and Z leadscrew calibration" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

- One thing I learned the most out of this class is fabrication skill. I’m now able to use all the machines with greater efficiency.
- Waterjet: I learned how to use the waterjet in general and perform calibration
- Mill: I learned and got better at different operations, including the use conversational programming to do various operations
- Lathe: I learned how to use both 3 jaws and 4 jaws chuck, as well as performing various operations (drilling, facing, boring, etc.)
- Using different measurement tools: force gauge, dial indicator, gage pin
- Creating a Process Plan before making parts to ensure the component is make-able and the process is well thought-out.
- Beside the listed measurements here - I also helped out with general measurements throughout the semester (including stiffness / runout, etc.)

## HTM
I was one of the main contributors to our group’s HTMs and was heavily involved in every part of the process

### Path Determination and Included Effect
[2.720 HTM Error Account List](https://docs.google.com/spreadsheets/d/1SY32hdd-_VY8citlE9APKeYPm67qquY3CeJ77KCd5zI/edit?usp=sharing)

We went through the process of determining appropriate structure loop, and accounting for what effects are available at each step

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/htm/path-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/htm/path-1.webp" alt="HTM structural loop and error list, 1 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/htm/path-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/htm/path-2.webp" alt="HTM structural loop and error list, 2 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/htm/path-3.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/htm/path-3.webp" alt="HTM structural loop and error list, 3 of 3" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### HTM Building Block Construction and HTM Assembly
I constructed HTM matrix functions for each type of error, including all contributions. This allows us to reuse it for ALL calculations going forward.

Then I constructed the main MathCAD files for both workpiece and toolside HTMs, and we went through revisions and perform various pressure tests to ensure our HTM is robust

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/htm/building-block-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/htm/building-block-1.webp" alt="HTM building block functions" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/htm/building-block-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/htm/building-block-2.webp" alt="HTM assembly in MathCAD" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

## CNC and Electronics

### System Diagram and Safety Process Plan
- I was the CNC integrator for my team, and was responsible for all aspects ‘electrical’ and CNC wise.
- Wiring diagram and Safety Process Plan is created to clearly communicate procedures and wiring plans.
- Robust CNC electronics integration: Soldered board is created to form a reliable connection, wires are labelled, heat shrinked properly and taped down, polarized and colored connectors are used.

[2.720 Electrical Safety Plan - Team Intuition](https://docs.google.com/document/d/1pKI2_VW_-C3Qy-2hXLHEu-p3LSv2FYZ2gOi5jL-gf8c/edit?usp=sharing)

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/cnc/system-1.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/cnc/system-1.webp" alt="CNC system and wiring diagram" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/cnc/system-2.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/cnc/system-2.webp" alt="CNC electronics" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

### Capability
- Utilize GRBL HAL open source with Teensy 4.1 + Teensy 3.2
- Tachometer for Speed Monitoring
- ESTOP and Limit Switches
- Closed Loop Speed Controller Logic in C++
- Music

### Video Demo (check them out):
Closed Loop Speed Control Test: [CNC Speed Control.MOV](https://drive.google.com/file/d/13NfMYyF3mnjU2-L73qy_pCDe0Q2yzeDO/view?usp=share_link)

<iframe src="https://drive.google.com/file/d/13NfMYyF3mnjU2-L73qy_pCDe0Q2yzeDO/preview" title="Closed loop speed control test" width="100%" height="420" style="border:0" allow="autoplay; fullscreen" allowfullscreen></iframe>

Automated (GCcode) Turning Operation with Closed Loop Speed Control Demo: [CNC Turning Demo with Speed Control.MOV](https://drive.google.com/file/d/1EFTX-6hAsvg6W3ALm4OMyrmZ-o1UNrow/view?usp=share_link)

<iframe src="https://drive.google.com/file/d/1EFTX-6hAsvg6W3ALm4OMyrmZ-o1UNrow/preview" title="Automated turning with closed loop speed control" width="100%" height="420" style="border:0" allow="autoplay; fullscreen" allowfullscreen></iframe>

### Cutting Tests
[Watch on Dropbox](https://www.dropbox.com/scl/fi/xbxfgsoa2wojvj5zqstkf/IMG_6888.mov?rlkey=ikenzrl77cme7z4jh4fpzedz1&dl=0)

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/results/turning.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/results/turning.webp" alt="Turning a stepped test part" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/results/part-metal.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/results/part-metal.webp" alt="Finished turned test part" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>

<div style="margin:18px 0;text-align:center"><a href="/images/272lathe/results/part-plastic.webp" style="box-shadow:none;display:inline-block;max-width:100%"><img src="/images/272lathe/results/part-plastic.webp" alt="Turned plastic test part" loading="lazy" style="display:block;margin:0 auto;max-width:100%;max-height:520px;width:auto;height:auto;border-radius:4px"></a></div>
