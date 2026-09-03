
### GitHub README

```markdown
# Arduino Analog Threshold LED

Simple Arduino project using a potentiometer as an analog input.

The Arduino reads the potentiometer value and switches an LED ON or OFF
depending on a predefined threshold.

## Components

- Arduino Uno
- Breadboard
- Potentiometer
- LED
- 220–330 Ω resistor
- Jumper wires

## Connections

### Potentiometer

- Outer pin → 5V
- Middle pin → A0
- Outer pin → GND

### LED

- D8 → resistor → LED → GND

## Code

```cpp
const int potPin = A0;
const int ledPin = 8;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(potPin);

  Serial.println(sensorValue);

  if (sensorValue < 500) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }

  delay(100);
}

How It Works

The potentiometer produces a variable voltage that is read through A0.

analogRead() converts the input into a value between:

0–1023

The program compares this value with a threshold of 500.

value < 500  → LED ON
value >= 500 → LED OFF

The current sensor value is also displayed in the Serial Monitor.

Main Concept
Analog input
    ↓
analogRead()
    ↓
threshold
    ↓
if / else
    ↓
digital output

The potentiometer acts as a manually controlled analog sensor.

A real analog sensor such as an LDR can later replace the potentiometer.

Learning Outcomes
Analog input
ADC values
analogRead()
if / else
Threshold logic
Serial communication
Digital output control
