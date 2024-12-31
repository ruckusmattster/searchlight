<h1>Guide to Finding and Reusing DLP Projectors for UHP Builds</h1>

This document outlines a step-by-step process for identifying and extracting suitable parts from used or broken DLP projectors. By following these guidelines, you can source a UHP (or similar arc-based) bulb, housing, power supply, and cooling components.

<h2>Searching for Used or Broken DLP Projectors</h2>
eBay and facebook marketplace are my go to's for sourcing parts. Look specifically for broken or “parts only” DLP projectors. Because you’re primarily interested in the bulb and its housing, don’t worry if the projector’s image is poor or if there are dead pixels. As long as the light still turns on, it’s viable.<br />
<br />
Pro Tip: Check listings for “blotchy image” “smudge in image” or “line through image” Often, these projectors still have intact bulbs and ballasts.

<details> <summary>photo info</summary> 1. a typical listing on ebay showing “for repair or parts” <br /> 2. the state of the projector doesn’t matter as long as it can power on and produce some light </details>

<h2>Check the Bulb Type</h2>

Visit Projector Central and look up the exact projector model. You can often find the specification sheet indicating the bulb type.
Compatible bulb types include UHP, P-VIP, UHB, and UHE 9or other manufacturer specific names). Each of these is a high-pressure mercury arc lamp that’s going to produce high intensity white light. The higher wattage bulbs generally have larger arc gaps and will be less intense but have more lumens.

<h2>Assess the Bulb Housing and Reflector Type</h2>

Once you confirm the projector model, look at photos or replacement part listings for the bulb’s housing.
Avoid bulb housings with a very narrow aperture or odd shapes; these can complicate alignment in your final build.
If the housing appears straightforward-like a simple reflector and mount then itll be easy to repurpose.<br />
<br />
Elliptical vs. Parabolic: <br />
  The light from a parabolic reflerctor is already collimated, light from a elliptical reflector is not.<br />
  A front lens clipped to the housing often indicates an elliptical reflector.<br />
  A parabolic reflector will have a open bowl shape.<br />
 

<h2>What to Keep</h2>
When your projector arrives, disassemble carefully to extract the following:<br />

The bulb and housing (including built-in glass filters that dont focus light). <br />
&nbsp; &nbsp; The filter is a plain appearing sheet of glass which filters UV from the output - this is important for safety.<br />
The power supply / ballast.<br />
&nbsp; &nbsp; In many projectors, this is a separate board driving the arc lamp - DO NOT MODIFY WIRING BETWEEN BULB AND BALLAST.<br />
Cooling fans.<br />
&nbsp; &nbsp;UHP lamps can exceed 1000°C internally, trust the manufacturers cooling design.<br />

Safety Note: Before handling, ensure the projector is unplugged and any large capacitors are fully discharged. UHP lamps are under high pressure—handle with care.

<h2>6. Basic Power Supply Setup</h2>

Simplest Method: Create high-voltage DC by wiring a full bridge rectifier to 240VAC (in regions with 240V mains), then place a suitable capacitor in parallel. This provides a ~340VDC supply. <br />
Power Factor Correction (PFC): If you’re experienced and have the resources, try reusing the projector’s built-in PFC stage. A well-implemented PFC can improve efficiency and allow for higher power operation (i.e., running multiple bulbs, or just running one more reliably).<br />
<br />
Important: High voltage is lethal. Ensure wires and connectors are properly insulated. A large capacitor can store dangerous charges even after the system is turned off.

<h2>Forcing the Ballast On</h2>
Most ballasts i know of use optocouplers for control signals. To activate the ballast without the original projector main board, you’ll need to find the right optocoupler and short its output side. <br />
Find the [optocoupler](https://w.wiki/CaN5) and identify its output using its datasheet to indentify which side is the output relative to pin 1 (which will be marked). Shorting the output side of the correct optocoupler simulates the mainboards turn-on signal. If you cant deduce which is the correct one, short one output and briefly power on. Repeat until the correct one's identified. Many ballasts' have a Eco mode where they draw half the power, use a watt meter at you 240vac supply to measure if its reaching the rated max power - as far as i can tell theres no benefit in using the Eco mode so get the maximum rated power out of your bulb.

<h2>Additional Tips</h2>

Testing the Lamp: Before you build a final enclosure, wire up the salvaged ballast and bulb. Verify it ignites and maintains steady brightness up to its rated power. <br />
Cooling Considerations: Use the projector’s original cooling fans and setup whenever possible. They’re designed specifically for this lamp’s heat load. <br />
Document and Label: Keep track of cable connections and any jumpers you bypass. Many ballasts use signals (like UART or I2C) to communicate with the main board. You may need to short or bypass these connections so the bulb can run independently. <br />

<h2>Conclusion</h2>

Repurposing a DLP projector for its UHP (or similar) bulb is a cost-effective way to access extremely bright and compact lighting solutions. By carefully selecting a projector with a suitable reflector, salvaging the correct components, and ensuring safe handling of high-voltage parts, you can assemble a powerful searchlight or high-intensity lamp with significantly reduced costs compared to buying everything new.
