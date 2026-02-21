

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
