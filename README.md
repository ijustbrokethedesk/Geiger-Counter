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

- It also lacks a built in display. I would like my counter to show the detected CPM without needing an external device to log the data.

- It only utilizes through-hole components due to being sold as a DIY kit. I would like to expand my options to include surface mount components as well.


## Design

My circuit can be broken down into 5 main sections.

- BMS / Power Circuitry
- Boost Converter
- Voltage Multiplier
- Buzzer Indicator
- LCD Display

### Battery Management System

### Boost Converter

### Voltage Multiplier

### Buzzer Indicator

### LCD Display