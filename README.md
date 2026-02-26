![RHIM2508](https://github.com/user-attachments/assets/4ce6f30f-9288-447d-8a91-70d91588e2f4)

![SITY5105](https://github.com/user-attachments/assets/4affd6e6-1416-44bb-b044-ade57a7789da)


YouTube - https://youtu.be/h-TxdCl6BcE

Instructables - https://www.instructables.com/7-Channel-Mixer-a-4-Channel-Option/

Here you can find everything you need to make your own 7 Channel Mixer.  This is based on Syntherjacks awesome little 4sum mixer which you can find a link below to.  My modular synth runs off 9/5V so this amp works perfectly for what I need.  You could also power it via traditional Eurorack style powering, you would just have to add a step down converter from the mixer to the 12V power source.

I have also included a Eurorack 4 channel version as well which will fit perfectly into any Eurorack.

https://syntherjack.net/portable-audio-mixer/


7 Channel Mixer - Circuit Explanation

This is a passive-input, op-amp buffered audio mixer built around an NE5532N dual op-amp. 

Here's how it works from input to output:


Input Stage (7 Channels)

* Each of the 7 channels (IN_1 through IN_7) follows the same structure. A 3-pin connector feeds into a 100K potentiometer (VOL_1 through VOL_7) which acts as the individual channel volume control. The wiper of each pot    connects through a 47K resistor to a common summing node. The 47K resistors serve as summing/isolation resistors — they prevent channels from loading each other and set the gain relationship between channels.


Summing & First Op-Amp Stage (IC1A)

* All 7 channel signals meet at the summing node, which connects through a 10µF coupling capacitor (blocking any DC offset) into the non-inverting (+) input of IC1A (the first half of the NE5532N). IC1A is configured as a unity-gain buffer with a 47K feedback resistor, providing a low-impedance version of the mixed signal. VREF is applied to bias the op-amp at the virtual mid-rail since this is a single-supply design.


Second Op-Amp Stage (IC1B) + Master Level

* The output of IC1A feeds into IC1B (the second half of the NE5532N). A 100K master LEVEL potentiometer in the feedback path of IC1B controls the overall output gain/volume. This gives you master level control over the entire mix.


Output Stage

* The output of IC1B passes through another 10µF coupling capacitor (again blocking DC) into an output volume pot and then to the OUT_1 connector.


Power Supply

* The circuit runs off a single +9V supply (PWR_9V connector). A BAT43 Schottky diode provides reverse polarity protection. Two 100µF filter capacitors smooth the supply rail. A resistor divider made of two 47K resistors creates a VREF mid-rail reference (~4.5V), which biases the op-amp stages so they can handle AC audio signals on a single supply. A LED with current-limiting resistor provides a power indicator.
