---
description: This page describes the system assembly instructions for Floyd SC carrier card
---

# 15 SYSTEM ASSEMBLY

## 15.1      General Description

1\.     Install Jetson module

2\.     Install heat sink or fan sink

3\.     Install optional fan on heat sink (if not already present)

## 15.2      Required Parts

![](broken-reference)

![](broken-reference)

## 15.3 Assembly Instructions

It is strongly recommended to use the DSC fan sink no. 6882601 or heat sink no. 6882604 for proper cooling. For higher temperature operation with high computing intensity, the fan sink is required.

See illustrations of heat sink, fan, and installation accessories below. The accessories are included with the heat sink.



![](broken-reference)

![4810010 Fan](broken-reference)

![Heatsink Accessories (TBU)](broken-reference)

### 15.3.1 Install Jetson Module

1\.     If not present on board, install 2 M2.5 x 6.5mm long spacers along board edge. If heat sink will be installed, also install 2 spacers next to module connector. See illustration.

![](broken-reference)

2\.     Insert module into socket at 45 degree angle. See illustration.

![](broken-reference)

3\.     Push down module so that both side latches click fully into position. You may need to push down on the module PCB and push in the latches because it is a tight fit. See illustration.

![](broken-reference)

4\.     If heat sink will not be used, insert 2 M2.5 x 10mm long screws through module into spacers. See illustration above.

### 15.3.2 Heatsink Installation

1\.     First install module as described above. All 4 spacers must be installed. Do not install screws into Jetson module yet.

2\.     Place appropriate thermal pad for the Jetson module being used into appropriate location onto bottom of heat sink. See illustration. The lining for each module is engraved on the heatsink. The TX2 NX and Xavier NX modules use larger pads, while the Nano module use the smaller one. Only one or the other pad is needed; discard unused pad. Remove one liner to place the pad onto the heat sink. Then remove the second liner before installing the heat sink onto the module. If you do not remove the second liner, the thermal performance of the heat sink will be greatly reduced. This is a common oversight.

![](broken-reference)

3\.     Place heat sink over module, aligning mounting holes with the 4 spacers on Floyd. Press down gently.

4\.     Install 4 M2.5 x 10mm long screws through the mounting holes into the spacers on Floyd. It is recommended to install all 4 screws loosely to ensure proper alignment, then tighten all 4 screws. See illustration.

![](broken-reference)

### 15.3.3 Install Fan

1\.     Place fan on heat sink in orientation shown in photo. Note the label is facing down (unseen in photo), and note the position of the 4-wire cable. In this orientation, air will blow down and out across the heat sink for improved heat dissipation.

![](broken-reference)

2\.     Install 4 M2.5 x 10mm long screws to hold fan in place. It is recommended to install all 4 screws loosely to ensure proper fan alignment, then tighten all 4 screws.

3\.     Plug fan cable into board connector J17. Note carefully the proper orientation of the fan cable connector. The solid side faces out, while the side with the 4 visible contacts faces in. The fan connector is delicate and can be difficult to insert by hand. We recommend to use fine pliers to aid in the installation. Alternatively you can install the fan connector prior to installing the module and heat sink for easier finger access, then install it over the heat sink as a final step.

![](broken-reference)

![](broken-reference)
