---
layout: post
title: 3D Printed Kinematic Mirror Mounts
---

The following is a guide on how to fabricate a low-cost alternative to commercial mirror mounts (around [$40 at their cheapest](https://www.thorlabs.com/thorproduct.cfm?partnumber=KM05)). Additionally, these allow you to customize your optics holder for any shape and size of optical element, which I found particularly useful as I was buying random surplus off of eBay. As a disclaimer, these mounts will have more thermal drift than anything commercial, and thus are less suitable for long-term experiments.

# Theory

Kinematic mirror mounts are optomechanical devices ubiquitous in optical systems as they provide the ability to precisely tune the direction of a laser beam. This is achieved through the use of [**kinematic couplings**](https://en.wikipedia.org/wiki/Kinematic_coupling), from which these devices get their name.

The kinematic coupling fixtures constrain a baseplate and optics holder to be aligned in a fixed and highly repeatable manner, by ensuring that there are exactly six points of contact between the two (restricting the six mutual degrees of freedom between them). The method of affixing the baseplate and optics holder together is typically either via extension springs (most common) or magnets (but never bolts, as this would defeat the purpose of having only six points of contact).

<figure style="float: right; margin-left: 20px; width:40%; height:auto;">
<img src="{{site.url}}/static/projects/mot/kinematics.gif"/>
     <figcaption style="text-align:center; font-size: 13px; margin-top:-15px;">A visual demonstration of how a kinematic mirror mount works</figcaption>
</figure>

The six points of contact in a kinematic mirror mount are given by three round-tip screws through the baseplate that contact grooves in the optics holder. As the screws are driven, they push against one side of the optics holder, forcing it to tilt slightly in that direction. Thus, if the optics holder is holding a mirror with a laser beam incident on it, the output beam directionality will shift correspondingly. The springs holding the two pieces together provide a restoring force to un-tilt the optics holder if the screw is loosened.

# Practice

## Tools Required

* SLA 3D Printer (FDM possible)
* Scotch Tape
* Epoxy

## Bill of Materials

* M4 or 6-32 Bushings x 3(~$0.10 x 3)
* M4 Ball-Tip Screws x 3(~$0.50 x 3)
* 1.5mm diameter, 6mm length dowel pins x 6 (~$0.25 x 6)
* 0.125in diameter, 0.5in length extension springs x 3 (~$0.80 x 3)
* M3 nut (~$0.02)  

## Fabrication
