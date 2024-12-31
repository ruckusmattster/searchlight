
 <h2>Introduction  </h2>

A High Pressure, Mercury, Short-Arc Searchlight. It boasts 20,000 [Iumens](https://en.m.wikipedia.org/wiki/Lumen_(unit)) and 9,300,000 [candela](https://en.m.wikipedia.org/wiki/Candela).<br />
[imgur album](https://imgur.com/a/qQ4Kzk7) of most of the photos taken

<h2>Core Components and Their Roles   </h2>

There are three key parts at play: the power supply, the ballast, and the [bulb](https://en.m.wikipedia.org/wiki/Ultra-high-performance_lamp).

First, the power supply: I built a custom one because l couldn't find anything commercially available at an affordable price. I used a [full bridge rectifier](https://en.m.wikipedia.org/wiki/Rectifier) (which converts AC into DC) and a capacitor to create a stable 340VDC supply using 240VAC input (in England we have 240V at the wall). For safety, I used a 1 mega-ohm resistor in parallel to the capacitor to enable it to slowly discharge after use; without that, the capacitor could store enough energy after powering off that it would be **fatal** if touched. Because of the high voltage, I had to ensure that everything was safe as any poorly insulated cables would pose a shock hazard. In future id like to build/buy a [PFC](https://en.wikipedia.org/wiki/Power_factor#Power_factor_correction_(PFC)_in_non-linear_loads) which would increase the efficiency. If myy current setup was more efficient it could support a second UHP bulb but due to the low power factor of my power supply its innefficiencys mean I'd be over the power limit.

![DIY PSU](https://i.imgur.com/0sNy9Xe.jpeg)
<details>
  <summary>photo info</summary>
  1. the PCB I assembled my PSU around, featuring a rectifier, 470uF 400V capacitor and a 1Mohm resistor on the back 
</details>


Second, the ballast, it provides the initial jump start of up to 25kv to get the bulb working, it also regulates power to the bulb. I bought both the ballast and bulb as part of a second hand projector from Ebay, this allowed me to keep the cost low. The ballast is controlled via the UART protocol hich is easily bypassed with a jumper wire.




Finally, the bulb: I used a UHP bulb which consists of a small [fused quartz](https://en.m.wikipedia.org/wiki/Fused_quartz) tube with a pocket of inert gases, mercury metal, and two electrodes. When the bulb is powered on, a short electric arc vaporises the mercury and excites the metal atoms. This excitation causes them to emit a wide spectrum of light. A bright 5mm LED typically draws 0.1W; by comparison, this bulb draws 250W, or 2500 times more power in a similar-sized footprint! (not including related cooling or focusing equipment)

![bulb](https://i.imgur.com/oaropD9.jpeg)
<details>
  <summary>photo info</summary>
  1. the final bulb I used, in the center is the quartz tube which is close to 5mm in diameter, around it is the reflector
</details>



This bulb is **incredibly** dangerous if mishandled. Internally, it heats up to 1000 Celsius (1800 Fahrenheit) and 200 times atmospheric pressure (3000 PSI) which, in case you didn’t realize, is *ridiculously high*. The fused quartz tube is used instead of glass because fused quartz can withstand higher temperature and pressure. However, without proper handling and cooling, if the fused quartz tube is overstressed, it could **explode** violently.

<h2>Reverse Engineering and Optics   </h2>

Normally, the ballast to run this bulb requires a connection to a projector motherboard; I spent a lot of time understanding and bypassing this. I bought my first ballast from a repair shop and used it in testing. Unfortunately, I very quickly killed it, so went to eBay for another one. With the second one I was quickly able to turn on the bulb and continued with the rest of the build.

![a shorted optocoupler to bypass the safety](https://i.imgur.com/DbxXLFG.jpeg)
<details>
  <summary>photo info</summary>
  1. one of of the jumper wires I installed to bypass a safety check 
</details>


Then I moved on to the optics. The most common is a [parabolic reflector](https://en.m.wikipedia.org/wiki/Parabolic_reflector) which creates a beam of *almost* parallel light. In a ideal world, the rays of light within the beam would be perfectly parallel, but small manufacturing inaccuracies and thermal expansion inside the bulb create sources of error, and I measured an angle of 2 degrees on my beam (which later can be used to estimate the spotlight’s size at different ranges). The larger the reflector is and the smaller the light source is, the tighter the beam is; the small errors become less significant. Despite all the sources of error, these bulbs are made with higher precision than most other lighting systems because they're typically used in projectors.




<h2>Final assembly and testing   </h2>

![a test setup](https://i.imgur.com/ohjZJRB.jpeg)
<details>
  <summary>photo info</summary>
  1. all the electronics laid out on a workbench I built so that i could test them while reverse engineering
</details>



To fulfill the mobile requirement of the contest I purchased the Bluetti EB3A, its pure sine wave inverter can output 600W and is perfect for this application.

Then came time to power up the final bulb assembly and start designing the case. I initially worked on building a case from scrap wood I found, but after finding a briefcase I've changed plans. I've abandoned the wooden case but will revisit it for a future project involving HID bulbs.

![1.2km ranged photo](https://i.imgur.com/Rjdmw7l.jpeg)

![beam from a while away](https://i.imgur.com/mWECayh.jpeg)

![final form factor](https://i.imgur.com/SohJunw.jpeg)

![beam side profile](https://i.imgur.com/gfR4mna.jpeg)

![warm flood led](https://i.imgur.com/RpTFNHU.jpeg)


<details>
  <summary>photo info</summary>
 1.an apartment building from 1.2km away <br />
 2. video of the beam during dense fog <br />
 3. the final form factor of the case and battery <br />
 4. side profile of the beam <br />
 5. the gtfc40 1800k in action <br />
</details>

I have recorded a (video)[placeholder] covering how i built the briefcase, searched for suitable projectors to take parts from, and some extra fun features I included. 

Using a [lux](https://en.m.wikipedia.org/wiki/Lux)meter and some math (as well as power measurements and lumen per watt values available online) I was able to determine the light’s intensity to be roughly 9.2 *million* candela, and output 17 *thousand* lumens. This delivers a range of 6km (3.7 miles), according to the [ANSI FL1 spec](https://en.m.wikipedia.org/wiki/Flashlight) (scroll to performance standards to see relevant information). For comparison, an average car’s high beams output 30,000 candela and 1500 lumens.

My target was to reach double digit ranges (in kilometres), but it feels okay for a first try; my second revision, which relies on different optics, is already in the works and should be much more intense.


<h2>Reflections and plans for the future  </h2>

This project went through a bunch of different phases. At first, I wanted to use an elliptical reflector UHP with a Fresnel lens using brand-new parts, but then I realized it’s way easier (and cheaper) to salvage from a second-hand projector. I also switched from a 12V lead-acid battery with an inverter to a Bluetti EB3A, and instead of the wooden box I built, I ended up using a briefcase for the final enclosure.

Looking back, I regret spending so much on new parts. Testing everything together from a used projector is simpler and gives you immediate proof that the parts work. I also avoided 3D printing because I wanted this to qualify for the handmade category of the competition. Had i used the 3d printer, I would’ve stacked some of the PCBs and saved a lot of horizontal space, making the whole thing more compact.

About six people asked me about commissioning lights, so I’ll work on making a V2 where I’ll focus on better workmanship (less glue more compact) and safety. I had a lot of analysis paralysis along the way (thanks and sorry to Luna and Dancho from the flashlight [Discord](https://discord.com/invite/yBnQ7mVa) for sticking with me). Even though it’s not on the same level as folks like Sma from TLF and CPF, I’m happy with its performance so far. I used mostly second-hand parts or scrap I scavenged from bins. If I’d had a bigger budget, I’d have replaced the entire panel around the bulb, potentially used two bulbs, and added a way to operate it remotely.

One major problem is weight distribution. The auxiliary light should really be in the back, and the power cord shouldn’t come out the back-it means I can’t tailstand the thing. After the competition, I plan to 3D print a hinged mechanism so it can tail stand. 

On the plus side, I love how it looks. The warm underglow aesthetic is cold, and speaker gives it a bit of whimsy. The user interface is also straightforward enough that most people can safely use the light, which was a big priority for me.


