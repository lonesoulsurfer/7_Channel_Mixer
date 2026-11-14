# 7 Channel Mixer (and a 4 channel Eurorack version)

This is an audio mixer for small modular synths. It has 7 input channels and one output. It uses an NE5532 op-amp and operates from 9 V. This repository also has a 4 channel version that fits in any Eurorack case.

![7 Channel Mixer](https://github.com/user-attachments/assets/4ce6f30f-9288-447d-8a91-70d91588e2f4)

![7 Channel Mixer front](https://github.com/user-attachments/assets/4affd6e6-1416-44bb-b044-ade57a7789da)

## Build guide and video

- Step-by-step build guide on Instructables: [7 Channel Mixer (+ a 4 Channel Option)](https://www.instructables.com/7-Channel-Mixer-a-4-Channel-Option/)
- Video on YouTube: [7 Channel Mixer](https://youtu.be/h-TxdCl6BcE)

## Two versions

| Version | Inputs | Use |
|---------|--------|-----|
| 7 Channel Mixer | 7 | My 9 V and 5 V modular synth |
| 4 Channel Mixer | 4 | Any Eurorack case |

The mixer operates from 9 V. To use Eurorack 12 V power, add a step-down converter between the 12 V supply and the mixer.

## What you need

- All parts are in the [parts list](Parts%20List.pdf).
- The schematics are in [Schematics](Schematics/).
- The Gerber files for the PCBs and the front panels are in [Gerber Files](Gerber%20Files/). You can send them to a PCB maker.

The mixer does not use a microcontroller. You do not need software.

## Build it

The Instructables guide shows each step, with photos. In short:

1. Order the PCB and the front panel for your version with the Gerber files.
2. Get the parts in the parts list.
3. Solder the parts to the PCB.
4. Attach the front panel.
5. Connect 9 V and test the mixer.

## How the circuit works (7 channel version)

The mixer has passive inputs and an op-amp buffer. It uses one NE5532N dual op-amp.

### Input stage (7 channels)

Each channel (IN_1 to IN_7) has the same circuit:

- A 3-pin connector sends the signal to a 100 kΩ potentiometer (VOL_1 to VOL_7). This is the channel volume control.
- The wiper of each potentiometer connects through a 47 kΩ resistor to a common summing node.
- The 47 kΩ resistors isolate the channels from each other, and they set the gain of each channel.

### First op-amp stage (IC1A)

- All 7 channels meet at the summing node.
- A 10 µF capacitor blocks DC, and it connects the node to the + input of IC1A (the first half of the NE5532N).
- IC1A is a unity-gain buffer with a 47 kΩ feedback resistor. It gives a low-impedance copy of the mixed signal.
- VREF biases the op-amp to the middle of the supply, because the circuit uses a single supply.

### Second op-amp stage (IC1B) and master level

- The output of IC1A goes to IC1B (the second half of the NE5532N).
- A 100 kΩ master LEVEL potentiometer in the feedback path of IC1B sets the gain of the full mix.

### Output stage

- The output of IC1B goes through a 10 µF capacitor (to block DC) to an output volume potentiometer, then to the OUT_1 connector.

### Power supply

- The circuit operates from one +9 V supply (PWR_9V connector).
- A BAT43 Schottky diode gives reverse polarity protection.
- Two 100 µF capacitors smooth the supply.
- Two 47 kΩ resistors make VREF, a reference at the middle of the supply (approximately 4.5 V). VREF biases the op-amp stages, so that they can process AC audio signals on a single supply.
- An LED with a current-limiting resistor shows that the power is on.

## Files in this repository

| Folder or file | Contents |
|----------------|----------|
| `Eagle_Files/` | Eagle files for both PCBs |
| `Front_Panel_Design/` | KiCad, Inkscape and DXF files for both front panels |
| `Gerber Files/` | Gerber files for both PCBs and both front panels, ready to order |
| `Schematics/` | Schematics of both versions |
| `Parts List.pdf` | Parts list |

## Credits

- Based on the [4sum portable audio mixer](https://syntherjack.net/portable-audio-mixer/) by Syntherjack.
- PCBs, front panels and the 7 channel and Eurorack versions: Marcus ([lonesoulsurfer](https://github.com/lonesoulsurfer)).

## Support

Do you like this project? You can support my work on [GitHub Sponsors](https://github.com/sponsors/lonesoulsurfer).

## Licence

This project uses the [CERN Open Hardware Licence v2, Strongly Reciprocal](LICENSE) (CERN-OHL-S-2.0). Copyright (c) 2025-2026 Marcus (lonesoulsurfer).

You can make, change and sell boards from these files. If you share or sell a changed design, you must also share the changed design files under the same licence.
