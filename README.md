# Low pass gate

@todo

## Parts required

| Count | Component | Where to buy |
| - | ------- | --------- |
| 1 | LPG board | tindie.com |
| 4 | LDRs[*](#light-dependent-resistive-opto-isolators-ldrs) | [See below](#light-dependent-resistive-opto-isolators-ldrs) |
| 10 | Inline jacks | [erthenvar.com](https://erthenvar.myshopify.com/collections/accessories/products/3-5mm-inline-jacks) and others |
| 2 | 3mm LED[†](#leds) |  |
| 4 | 100KΩ Pot |  |
| 1 | 3 pin 2.54mm header |  |
| 1 | 2 pin 2.54mm jumper |  |
| 1 | IDC 10 pin power connector |  |
| 1 | IDC 10 pin → 16 pin eurorack power cable |  |

----

## Part choice

#### TL;DR
*Use 4 NSL-32SR3*. They are affordable – compared to the alternatives – easily available to hobbyists through Digikey, and offers a very musical response time from the 'pluck' gate input.


### Light dependent resistive opto-isolators (LDRs)

The heart of the module! Photo resistive opto-isolators, also known as Vactrols – referred to here as LDRs – are the crux of the low pass gate, simultaneously attenuating the input signal and filtering it through a mild low pass filter.

Compared to most other electronic components, LDRs are very slow to respond. The time it takes to turn one on and off is typically measured in tens (or hundreds) milliseconds. These timescales are that of notes and rhythms, unable to cope with audio rate signals. The resistors in LDRs have different chemical composition, and require careful choice to get musical results. And LDRs are expensive and difficult to buy; they contain heavy metals (cadmium), and the number of manufacturers willing to produce these components is sometimes unpredictable. Despite all of this, they have great electromusical applications. Their slow speed often matches that of physical systems, with a quick attack and slow logarithmic decay, and different LDRs can be used for different effects. Fickle, expensive, poisonous, and musical!

In this module, LDR1–4 are responsible for the variable filter response of the low pass gate. The choice of LDR may effect both the attack/decay time of the filter and the tone produced.

#### On resistance
On LDR datasheets, this value is commonly listed at several currents. Higher currents means more light from the LED light source, and lower resistance, albeit in a very non-linear fashion. In this module, the default current driven through each LDR is 12mA.

The closer to 0Ω the on-resistance reaches, the less the audio signal will be filtered. Any resistance over 100Ω is will result in an audible filtering at all settings, and as such, its important that when the control circuit turns the LDRs on, 12mA through your LDR must produce less than 100Ω.

Test this value yourself before assembly. LDR datasheets aren't always accurate, and this value can vary  between otherwise identical LDRs.

#### Off resistance
LDR off resistances typically range from 1MΩ to 10MΩ+. Anything above 800KΩ should work fine here, and unless you’re building your own LDRs, this value can usually be ignored.

#### Filter LDR recommendations
| LDR Model | Availability | Comment |
| ------------ | ------------- | ---- |
| NSL-32SR3    | [Digikey](https://www.digikey.com/product-detail/en/luna-optoelectronics/NSL-32SR3/NSL-32SR3-ND/5039793) | Excellent response. Recommended. |
| NSL-32SR2    | [Digikey](https://www.digikey.com/product-detail/en/luna-optoelectronics/NSL-32SR2/NSL-32SR2-ND/5039808) | Slower decay than 32SR3, but difference is not obvious. Recommended. |
| Vactrol VTL5C3 | ?? | Fast response, sounds nice. No longer manufactured. |
| XVive VTL5C3 | [Cabin Tech Global](cabintechglobal.com/prod_VTL5C3-2.html) | Datasheet claims on-resistance 5Ω @ 10mA, but tested at 1KΩ. *Not recommended* |

#### LDR for mute circuit.
On resistance is not as critical in the mute position, as nearly any resistance <1KΩ will result in the filter cutting off the audio signal. A slower LDR response can be more desirable here.
There isn't a lot of space on the PCB for larger packages; please use Silonex LDRs (NSL-32SR3, NSL-32SR2, etc).

### LEDs
The two indicator LEDs reflect the drive signal for each channel. The forward voltage of the LEDs isn't particularly important – the drive circuit can easily provide up to 4V of voltage drop per LED – but current through these LEDs is identical to each pair of LDRs. Because the indicator LED current and LDR current can't be set independently, it's important to choose LEDs that have a acceptable brightness when driven in the range 0mA – 12mA.

----

## Assembly

[Image of board front and pack](url)
Front of the PCB = White silk screened logo, no SMD components
Back of the PCB = Gold US Knitting logo, many SMD components

1. Solder LDR1–4 to the front of the PCB. Footprints for LDR have three round pads, and one square (also marked with cutoff corner on silkscreen). The *positive* pin of the LDR must be soldered to the *square pad*. [LDRs in added to board](url)
1. Insert all 10 jacks and 4 potentiometers to the front of the PCB. [Electromechanical components added to board](url)
1. Place panel over front of panel, and tighten potentiometer nuts to lock panel position in place. [Panel added to board](url)
1. Very carefully flip PCB over, and solder these components to board with panel attached.
1. Remove front panel. [Board with panel removed](url)
1. Solder power connector to back of PCB. If using keyed header (recommended) make sure notch is on the outside of the board. [Power connector attached to board](url)
1. Solder 3 pin 2.54 header to pads on back side of board. [Header attached to board](url)
1. Add jumper to header. Linking top two pins will normalize 2nd channel input to 1st channel input. Linking bottom two pins will normalize 2nd channel input to GND. [Jumper settings](url)
1. Add LED1 and LED2 to front of board, with the *long pin* of each LED inserted into the *square pad*. [LEDs added to board; bottom LED with bent leads](url)
1. Place panel back on front of board, and confirm that LED1 and LED2 are aligned with front panel. Solder LEDs to board. [LEDs placed correctly under panel](url)
1. Trim any remaining leads from back of board. Attach 10pin to 16 pin IDC power cable. Wash your hands and have a cup of tea.

### Troubleshooting
1. Check power connector orientation. If the power connector is temporary reversed, the module shouldn't be damaged, but it will not work!
1. Confirm that the filter LDRs and indicator LEDs are correctly oriented. If any of these LED-based components are not inserted in the correct orientation, the channel will not pass any signal.


## Further hacking
#### Change filter LDR current
The value of R9/R27 sets the filter LDR current, approximately 12V/R mA. To make this value easier to adjust, remove R9/R27, add small value resistors to R6/R23 and solder 5K trim pots to LEDI1/LEDI2.

#### Change pluck response time
The pluck circuit turns a gate signal into a brief trigger pulse. The pulse length is set by a RC high-pass filter that feeds into a comparator. Change C1/C12 and R12/R29 to adjust the filter frequency, or change the comparator set-point by adjusting R8/R25 & R13/R30.

----

# Operation
Each channel is identical in operation.
[Channel diagram](url)

## Controls
The CTRL input opens the low pass gate.
If nothing is plugged into the CTRL input, turning the Control knob clockwise manually opens the low pass gate. Otherwise, the Control knob will attenuate the CTRL signal.
A positive gate signal passed to the PLUCK input will very briefly open and then close the low pass gate, 'plucking' the LDRs. A similar effect can be generated by passing a short trigger signal to the CTRL input.

The MUTE input dampens the output signal. Small voltages (0-2V) will provide largely tonal variations; large voltages (5V-10V) will come very close to completely muting the output.
If nothing is plugged into the MUTE input, turning the Mute knob clockwise will gradually mute the audio signal. When the MUTE input is used, this knob will attenuate the MUTE signal.
