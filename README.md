# SeaCell
SeaCell is a simple combination of hardware that keeps phones powered and connected to the cell network while underwater.  This allows us to use all the features of a cell phone -- sensors, camera, microphone, livestreaming -- while the phone is in an aquatic environment.  SeaCell is a combination of three devices -- a commercial underwater phone housing, a seaCell adapter that attached to the underside of the phone housing and sends power and data to the phone through the walls of the housing, and a solar surface buoy that provides power and data to the seaCell adapter via a coax cable.

![architecture](https://github.com/Ex-press/SeaLink/blob/main/Images/connected%20buoy.png#:~:text=Raw%20file%20content-,Download,-%E2%8C%98)

Cellular infrastructure is incredible, and it covers a *huge* percentage of the area of coastal and watershed waters.  Something like 70% of coastal waters worldwide -- up to 12 miles offshore -- are within cell phone range, and ~60% of all the watershed land that drains into those coastal waters has cell coverage.  Those are worldwide numbers -- where we developed the early designs, in the Northeast US, 85% of coastal waters and >90% of watershed area has cell coverage.  In addition, those coastal waters are pretty shallow -- >85% of the area of bays and sounds around us are shallower than 130ft, and you can put a phone on the bottom there in a housing that costs about $100.  For a couple hundred more dollars, you can go down to 280ft with commercially available phone housings, meaning, generally speaking, if the water is within cell phone range, you can put a phone on the bottom with a commercially available housing (with the exception of those lucky people living right next to fjords and undersea canyons).  

There are two key limitations to putting a phone underwater:  power and connectivity.  With no additional power, a phone will run just out of battery, limiting the length of time it can do anything useful.  Additionally, once you're more than a few centimeters underwater, the water will block the RF signals that a phone needs to communicate with a cell tower, cutting off the phone from the rest of the world.  SeaCell does two things:  it brings power and cellular data from a surface buoy down to the cell phone, and it sends both power and data *through the walls* of the phone's dive housing, *without* modifying the housing.  How do you do this?  Well, getting power down there is easy -- a solar panel on the surface collects energy and stores it in a battery via a device called a charge controller, and this lets us take DC power, day or night, and connect it to a waterproof cable that we drop down to the bottom.  Cell data is a little trickier, but there is a convenient device, called a cell signal booster, that is designed to re-broadcast a cell tower in a small area, like a house or office in a rural area, extending coverage to that area.  We put a cell signal booster and antenna in the surface buoy, but rather than using an antenna at the surface to re-broadcast the signal, we connect the signal booster to a piece of coaxial cable that we drop down to the bottom.  Coaxial cable is a great cable, and we can actually use one cable to send both the power and data signals.


But how do we get the power and data from the coax cable to the phone?  Well, as it turns out, most modern cell phones have the capability to wirelessly connect to power and data.  The power works by a wireless charging standard called Qi, which is included in many modern cell phones, and lets them charge on a charging mat like you might find in a car or cafe.  Those charging mats are themselves built around a standardized piece of electronics equipment called a Qi transmitter module -- this takes DC power and wirelessly sends it through a few millimeters of plastic into a phone, and as it turns out, those modules work great at sending power through a dive housing.  Continuing the trend of extreme affordability that we try to follow everywhere in this design, those modules cost about $1.

![qi modules](https://raw.githubusercontent.com/Ex-press/SeaCell/refs/heads/main/Images/qi%20modules.jpg)

Sending data wirelessly is even easier -- cell phones all have cellular radios.  The coax cable does a good job shielding the cellular signal from the surrounding water, and at the end of the cable, all we need to get the data between the cable and the cell phone is an antenna.  The simplest antenna we can make is called a quarter-wave monopole antenna, and it's just a piece of wire.  All we have to do to make this antenna is to know how long to make our wire, which is based on the frequency of the cell phone radio -- around 900mhz for 4G.  With the simple formula c = wavelength * frequency, we can figure out the wavelength of a 900mhz radio wave (33cm), and we can cut our wire to a quarter of that wavelength, or 8.3cm.  

![no-penetrator connections](https://raw.githubusercontent.com/Ex-press/SeaCell/refs/heads/main/Images/no-penetrator%20details-04.png)

It's worth mentioning -- this is different from the traditional ocean engineering approach to bringing signals into an electronic device underwater.  The traditional approach is to make a custom depth housing, with devices called cable penetrators that carry power and data wires from the surface into the pressure housing, where you make your connections and do whatever you have to do.  As soon as you start making custom housings, the costs tend to go up quite quickly, into the thousands of dollars.  Our approach here is to use an un-modified commercial housing rather than making a custom housing, and put our components *outside* the housing.  How do you keep the components dry without making a custom housing?  You *pot* them -- put them in the right place and then cover them with waterproof epoxy goop.

![potted qi module](https://raw.githubusercontent.com/Ex-press/SeaCell/refs/heads/main/Images/potted%20qi%20charger.jpg)


The takeaway here is that, at this point in time, we have a wide assortment of lego pieces that are commercially available, and can be combined in a pretty simple to connect an underwater phone to power and data.  This readme should give you an overview of the whole process, but to get into the details, this project is made up of three key parts:  the surface buoy, the underwater seaCell device, and the depth housing.  Each of these parts has further documentation below:

* [surface buoy](https://github.com/Ex-press/SeaCell/tree/main/Buoy)
* [seaCell device](https://github.com/Ex-press/SeaCell/tree/main/Hardware)
* [depth housing and mount](https://github.com/Ex-press/SeaCell/tree/main/Housings)


SeaCell is an open-source hardware project, which means that all of the design source files are available.  The project is released under a GPL license, which means that you are free to use and modify it, even commercially, but you must share a link to the source code and release any modifications you make to the project under the GPL license as well. 


---------------------


This project introduces a simple, open-source way to keep a phone powered and connected while underwater, simply using some low-cost, commercially-available parts in a novel way.  


This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see <https://www.gnu.org/licenses/>.