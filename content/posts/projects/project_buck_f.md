---
author: "Kiet Vu"
title: "★ 50 - 150W Buck Converter Paper Design"
date: "2025-05-15"
description: "Power Electronics (MIT 6.334) Final Design Project"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
weight: 3
---

(Complete work is included in the ["Details"](#details) section below)

As part of MIT's Power Electronics (6.6220, also known by its old number 6.334), my task was to design a buck converter that meets a variety of requirements. This project touches on a variety of practical considerations when designing a switched-mode power converter (it also serves pretty well as a comprehensive review of the class material).

For this project, there were a range of considerations that need to be addressed — here are some of them:

- Component ratings
- Magnetic design for the EMI filter and output filter inductors, which includes (gapped) core selection, number of turns, and wire gauge. These selections were made to ensure appropriate inductances and to prevent the inductors from saturating during operation.
- Semiconductor losses, which include diode loss, MOSFET conduction and switching losses
- Losses associated with magnetic components, which come in three forms: conduction losses, skin depth effect (at high frequency, AC current flows primarily near the conductor surface, increasing the effective resistance), and core loss.
- Thermal design: ensuring that the junction temperature of each semiconductor component does not exceed its rated temperature (150°C)
- EMI filter performance and stability across different operating conditions
- Feedback controller design: maintaining ample phase and gain margin across all operating conditions

One of my plans is to lay out this converter on a PCB and verify its performance—I think that would be a very satisfying conclusion to this project! Overall, I found the class to be a valuable experience that helped me better understand the various design considerations (and how to actually calculate them!) that go into designing a power converter.

## Details 
The Full Problem Description: 
![Problem Description](/images/6622_problem_desc.png)
The complete document can be found here (The full MATLAB code can be found at the end of the document):
<embed src="/pdfs/buck-conv-6622.pdf" type="application/pdf" width="100%" height="600px" />
