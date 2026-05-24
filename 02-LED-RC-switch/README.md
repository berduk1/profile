# LED + Resistor + Capacitor + Switch Circuit

This is a simple RC circuit simulation made in Falstad.

## Circuit components

- 5 V voltage source
- Switch
- Resistor
- LED
- Capacitor
- Ground

## Circuit idea

The switch connects and disconnects the voltage source.

When the switch is closed, the capacitor charges and the LED turns on.

When the switch is opened, the voltage source is disconnected, but the capacitor is still charged. The capacitor then discharges through the resistor and LED, so the LED stays on for a short time and slowly fades out.

## Basic schematic

```text
5V → switch → ● → resistor → LED → GND
              │
          capacitor
              │
             GND
![LED RC switch circuit](02-LED-RC-switch/images/led-rc-switch.png)
