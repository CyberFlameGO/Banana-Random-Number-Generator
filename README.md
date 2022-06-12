# Banana Random Number Generator
[![License: CC BY-SA 4.0](https://img.shields.io/badge/Hardware%20license-CC--BY--SA%204.0-brightgreen.svg)](http://creativecommons.org/licenses/by-sa/4.0/)  
[![License: GPL v3](https://img.shields.io/badge/Firmware%20license-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

![brng](bnrg.jpg)

## Project description 
An Arduino based true random number generator. Takes it's peculiar name from the potassium-40 present in bananas, used as radiation source for the random number generatation.  
  
_Disclaimer: the radioactivity from the bananas doesn't quite make the difference, the background radiation is more than enough to make the generator work. Potassium is definitely detected, some tests conducted with pure KCl and KOH showed a huge increase in the detector activity._

![layout 1](/images/layout.png)

1. [Project status](#project-status)  
1. [Hardware](#hardware)  
1. [Software](#software) 
1. [Enclosure](#enclosure) 

## Project status 
The current release is fully working. 
## Hardware 
The hardware is based around the popular ATMega328P and the STS-5 (a.k.a. CTC-5) Geiger-Müller tube.
## Software

As of this moment there are available two versions of the firmware:
- **minimal_test.c**: this version is fully compatible with the unmodified hardware. It uses the hardware interrupt INT0 and has proven to be unreliable when brought into an arduino environment due to interferences with the millis() function from the Wiring core. On it's own works with no problems. [Read more on this, in italian](https://www.valerionappi.it/chi-quadro/)
- **minimal_test_with capture.c**: this version and has proven to be much more reliable than the previous, since it captures the timer stamp via dedicated hardware and it's not subject to software delays. It's based on the timer capture function on PB0/ICP1 pin of the ATMega. This version needs a bodge wire between pin PD2 and pin PB0, as shown below:  

![mod](/images/bodge.jpg)

I'm currently working on an arduino version on the software, that will be published in this repo as soon as it gives consistent results.
In the future another version of the firmware which makes use of the hardware as a plain Geiger counter might be developed. Any help is welcome!
## Enclosure
The board is designed to fit in a laser cut acrylic enclosure to protect the user from the high voltage present onboard. 
The enclosure design files are included and licensed under [CC-BY-SA 4.0 license](http://creativecommons.org/licenses/by-sa/4.0/)  
