# Geiger Counter

Working in the nuclear industry during my internship has inspired me to research how some of the tools we use on a daily basis work at a low level.

Most notably is the geiger counter, a device which helps us identify and measure radological samples or contamination. I figured the best way to learn about how it works is to actually build one myself.

## Requirements

I have set the following project requirements for myself.

1. Must be battery powered and rechargable via USB-C
2. Must cost less than the average handheld geiger counter (~$100)

## Preliminary

I started by reading a variety of literature on the workings of a geiger counter and exploring multiple published schematics. Since I have never attempted a project like this before, I wanted to gain some inspiration from existing designs. I eventually encountered this [*Open Sourced Design*]() which is sold as a kit, and is a good compromise between functionality and pricing.

It features two 555 timers, one for driving the boost circuit and another as a pulse generator. This is perfect as it avoids the current parts shortage affecting boost controller ICs. Finding ways to use the same type of component multiple ways in a circuit is also optimized for mass production.

There were a few areas of improvement that I had with this circuit:

- It was created in 2014. With adequate component research and selection, I believe I can source better components

- It lacks a built in display. I would like my counter to show the detected CPM without needing an external device to log the data.

- It only utilizes through-hole components due to being sold as a DIY kit. I would like to expand my options to include surface mount components as well.


## Design

My circuit can be broken down into 5 main sections.

- BMS / Power Circuitry
- Boost Converter
- Voltage Multiplier
- Pulse Detector
- LCD Display

### Battery Management System

I plan on powering this circuit using a 3.7V Li-Ion battery, rechargable through a 5V USB supply.

- Found suitable 5V Boost converter IC, removed 3V LDO


### Boost Converter

> I recognise that designing a boost controller using a 555 is a bad design, however at the time of this project there is a massive parts shortage affecting power management ICs, and as such I had to improvise. See the notes section for more details.

To design the boost stage of the geiger counter, we determine the input voltage, output voltage, and output current specifications of the boost converter. This circuit uses a combination of a boost converter and voltage multiplier to turn the 5V input into a 400V supply for the GM tube. 

As I am using a 3 stage multiplier, the boost stage only needs to output 133V. However, as the multiplier increases the output voltage, the maximum output current will be lower than the input. To assume a generous margin I rate the current consumed by the GM tube circuit to be 1mA.

$V_{in} = 5V, N = 3$

$V_{out} = \frac{400V}{N}=133V$

$I_{out} = (N)(1mA) = 3mA$


$\Delta I_L
\approx (0.4)(I_{out})(\frac{V_{out}}{V_{in}})
\approx 31.92mA
$

---

Frequency calculations of the 555.

$f_{sw} = \frac{1.44}{(R_1+2R_2)C} = 14.6kHz$

---

Inductor Rating

$L = \frac{V_{in}*(V_{out}-V_{in})}{V_{out}*f_s*\Delta I_L} \approx 10mH$



### Voltage Multiplier

- Fixed poor math skills

### Pulse Detector

Case 1 (Tube Non-Conducting):

- Transistor is off
- Bias resistors pulled to ground

Case 2 (Tube Conducting):

- Top bias resistor produces a voltage across itself due to current impulse
- Bottom bias resistor to form voltage divider where $V_{out} > 0.7$
- Capacitor for RC filtering
- Quench resistor to prevent continous conduction

### LCD Display


## Notes