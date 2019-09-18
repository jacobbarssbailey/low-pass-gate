# Dual low pass gate

This project provides tested plans for a 8HP Eurorack-format Dual Low Pass Gate.

![Assembled module](/media/glamour.jpg)

## BOM

| Qty | Device | Value | Package | Parts | Notes |
| --- | ------ | ----- | ------- | ----- | ----- |
| 8 | Resistor | 1K | 0603 | R7, R9, R11, R15, R24, R27, R28, R32 | |
| 4 | Resistor | 47K | 0603 | R13, R17, R30, R34 | |
| 4 | Resistor | 10K | 0603 | R4, R14, R20, R31 | |
| 4 | Resistor | 100K | 0603 | R8, R16, R25, R33 | |
| 12 | Resistor | 200K | 0603 | R1, R2, R3, R5, R10, R12, R18, R19, R21, R22, R26, R29 | |
| 2 | Capacitor | 100p | 0603 | C3, C12 | |
| 8 | Capacitor | 100n | 0603 | C1, C5, C6, C8, C10, C15, C16, C19 | |
| 4 | Capacitor | 560p | 0603 | C4, C13, C21, C22 | |
| 2 | Capacitor | 1µ | 0603 | C2, C11 | |
| 2 | Capacitor (Pol) | 47µ–100µ | Panasonic D | C14, C18 | |
| 4 | Pot | 100K | ALPS 9mm Vert | GAIN1, GAIN2, RMUTE1, RMUTE2 | |
| 10 | Audio Jack (Mono) |  | Inline | CTRL1, CTRL2, IN1, IN2, MUTE1, MUTE2, OUT1, OUT2, PLK1, PLK2 | [Erthenvar](https://erthenvar.myshopify.com/collections/accessories/products/3-5mm-inline-jacks) and others |
| 2 | Quad Op Amp | TL074 | SO14 | U1, U2 |  |
| 2 | Comparator | LM397 | SOT23-5 | IC2, IC5 |  |
| 8 | Schottky Diode |  | SOD323 | D1, D2, D3, D4, D5, D6, D7, D8 |  |
| 6 | Light Dependent Resistor | SR32-SR3 | VTL5C-SMALL | LDR1, LDR2, LDR3, LDR4, LDR5, LDR6 | [digikey.com](https://www.digikey.com/product-detail/en/advanced-photonix/NSL-32SR3/NSL-32SR3-ND/5039793) and others |
| 1 | 10 pin Power |  | 10 pin shrouded IDC 2.54mm pitch | P1 |  |
| 2 | LED[†](#leds) |  | 3mm | LED1, LED2 |  |

#### †LEDs
In the drive circuit, indicator LEDs and LDRs are driven in series, with identical current. For best results, use LEDs that have a acceptable brightness when driven in the range 0mA – 12mA.

### Assembly [important!]

The pairs of jacks IN1 & CTRL1 and IN2 & CTRL2 share a ground pin connection. Make sure to check CTRL1 and CTRL2 orientation before soldering.


## Operation and Controls

![Panel with labels](/media/lpg-panel.png)

Each channel of the gate/filter is identical, save that Channel B's Audio Input is normalled to Channel A's.

 The control knob opens the filter and allows audio to pass. It attenuates the Control CV (normalled to =6V).

Pluck CV is a gate-to-trigger converter feeding the control circuit. Gate signals sent to this input will 'pluck' the control circuit, causing it to ring out.

 The mute input (normalled to =10V) will both shorten the response time of the filter, and apply a very mild hi-pass filter. In a musical sense, its effect on the filter is akin to softly holding a palm against a rung bell or plucked string.

 At very low values, near 0V the mute input will allow some audio to pass through the circuit without any control input. If this isn't desired, turn the mute knob up to 15-20%.


## Other notes

Increasing the capacitance of C21 and C22 will increase the resonance of the low pass filter. Quite strong filter resonance is achievable by changing this component value.

Other LDRs/Vactrols may work equally well. If test any and have particular recommendations, please open an issue here.
