
---

# 2. GitHub README

Ovo bih stavio kao puno čišći README.

```markdown
# Arduino Two-LED Toggle Button

Arduino exercise using one push button to alternate between two LEDs.

Each valid button press toggles the active LED:

- LED1 ON / LED2 OFF
- LED1 OFF / LED2 ON

## Components

- Arduino
- Breadboard
- 2 LEDs
- 2 × 220–330 Ω resistors
- Push button
- Jumper wires

## Pin Configuration

| Component | Arduino Pin |
|---|---:|
| Button | D2 |
| LED1 | D8 |
| LED2 | D9 |

The button uses the Arduino internal pull-up resistor:

```cpp
pinMode(buttonPin, INPUT_PULLUP);

Therefore:

button released = HIGH
button pressed = LOW
Circuit
LED1
D8 → resistor → LED1 → GND
LED2
D9 → resistor → LED2 → GND
Button
D2 → push button → GND

Code
const int buttonPin = 2;
const int led1Pin = 8;
const int led2Pin = 9;

bool led1State = true;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(led1Pin, OUTPUT);
  pinMode(led2Pin, OUTPUT);

  digitalWrite(led1Pin, HIGH);
  digitalWrite(led2Pin, LOW);
}

void loop() {
  if (digitalRead(buttonPin) == LOW) {
    delay(30);

    if (digitalRead(buttonPin) == LOW) {
      led1State = !led1State;

      digitalWrite(led1Pin, led1State);
      digitalWrite(led2Pin, !led1State);

      while (digitalRead(buttonPin) == LOW) {
      }

      delay(30);
    }
  }
}
How It Works

The Boolean variable:

bool led1State

stores the current state.

Each confirmed button press executes:

led1State = !led1State;

which toggles the stored value.

LED1 follows led1State:

digitalWrite(led1Pin, led1State);

LED2 receives the inverse value:

digitalWrite(led2Pin, !led1State);

This guarantees that only one LED is ON at a time.

Debouncing

A short delay is used to reduce mechanical button bounce:

delay(30);

The button state is then checked again before changing the LED state.

The program also waits until the button is released:

while (digitalRead(buttonPin) == LOW) {
}

This ensures one toggle per physical button press.

Troubleshooting

During testing, the second LED branch initially failed.

The problem was isolated by checking:

LED
Arduino output pin
resistor
jumper wire
breadboard connections

Replacing the resistor and jumper wire solved the issue.

This demonstrated the importance of testing one component at a time instead of changing the entire circuit.

Connection to Digital Logic

The Boolean variable behaves similarly to the stored state Q of a flip-flop.

led1State  ≈ Q
!led1State ≈ Q̅

The button press acts as the event that changes the stored state.

This makes the project a useful software analogy to the toggle behavior of a JK flip-flop.

Screenshots

![Toggle Button with two Leds](screenshots/Two-Led.png) 

Learning Outcomes
Digital inputs and outputs
INPUT_PULLUP
Boolean state variables
Toggle logic
Complementary outputs
Button debouncing
Waiting for button release
Basic hardware troubleshooting
Connection between software state and digital logic
