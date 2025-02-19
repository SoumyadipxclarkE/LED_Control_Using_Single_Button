LED Control Using Button (Arduino)
Description

This project uses an Arduino to control an LED using a button. The LED is toggled between ON and OFF states each time the button is pressed. The button press is debounced to avoid multiple toggles from a single press.
How It Works:

    The program continuously checks the state of the button.
    When the button is pressed, the state of the LED (connected to pin 8) is toggled (ON if it was OFF, and OFF if it was ON).
    A debounce delay of 200 milliseconds ensures that the button press is not registered multiple times due to mechanical bouncing of the button.

Hardware Setup:
Required Components:

    1 Arduino board (e.g., Arduino Uno)
    1 LED
    1 220Ω resistor (for current limiting)
    1 Push button
    Breadboard and jumper wires
    Power supply (Arduino powered via USB or external adapter)

Circuit Diagram:

    LED:
        The anode (long leg) of the LED connects to pin 8 of the Arduino.
        The cathode (short leg) connects to the GND pin on the Arduino through a 220Ω resistor.

    Button:
        One terminal of the button connects to pin 5 of the Arduino.
        The other terminal connects to GND.

Code Explanation:

int ledPin = 8;             // Pin connected to the LED
int ledState = LOW;         // Initial state of the LED (OFF)
int buttonPin = 5;          // Pin connected to the button
int buttonState = 0;        // Variable to store the current button state
int lastButtonState = LOW;  // Variable to store the last button state

Variables:

    ledPin: Specifies the pin number to which the LED is connected (pin 8).
    ledState: Stores the current state of the LED (either LOW or HIGH).
    buttonPin: Specifies the pin number to which the button is connected (pin 5).
    buttonState: Stores the current state of the button (either HIGH or LOW).
    lastButtonState: Stores the previous state of the button to detect changes (button press).

void setup() {
  pinMode(ledPin, OUTPUT);   // Set LED pin as OUTPUT
  pinMode(buttonPin, INPUT); // Set button pin as INPUT
}

setup():

    pinMode(ledPin, OUTPUT): Configures the LED pin (pin 8) as an output to control the LED.
    pinMode(buttonPin, INPUT): Configures the button pin (pin 5) as an input to read the button state.

void loop() {
  buttonState = digitalRead(buttonPin);  // Read the current button state

loop():

    buttonState = digitalRead(buttonPin): Continuously reads the state of the button (either pressed or not pressed).

  if(buttonState == HIGH && lastButtonState == LOW) {
    ledState = !ledState;                // Toggle the LED state
    digitalWrite(ledPin, ledState);      // Update the LED based on the new state
    delay(200);                          // Debounce delay
  }

Button Press Detection:

    if(buttonState == HIGH && lastButtonState == LOW): This condition checks if the button has just been pressed. The button's state has changed from LOW (not pressed) to HIGH (pressed).
    ledState = !ledState;: This line toggles the current state of the LED. If the LED was OFF (LOW), it turns ON (HIGH), and vice versa.
    digitalWrite(ledPin, ledState): Updates the LED state to the new value of ledState.
    delay(200): Adds a short delay (200 milliseconds) to prevent multiple readings from the button due to mechanical bouncing (debouncing).

  lastButtonState = buttonState;   // Save the current button state for the next loop
}

Update Button State:

    lastButtonState = buttonState;: Updates the lastButtonState to store the current state of the button, so the program can detect the next transition (button press).

Step-by-Step Workflow:

    Initialize Pins:
        The setup() function sets the LED pin as an output and the button pin as an input.

    Loop Starts:
        The loop() function begins, continuously checking the button state.

    Button Press Detection:
        Each loop cycle, the program reads the current state of the button.
        If the button has been pressed (transitioning from LOW to HIGH), the LED state is toggled.

    LED Update:
        The LED is updated to match the new state (ON or OFF) using digitalWrite().

    Debounce Delay:
        The delay(200) ensures that the button press is only registered once for each press.

    Repeat:
        The loop() function repeats, and the process continues indefinitely.

Usage:

    Upload Code: Upload the provided code to your Arduino using the Arduino IDE.
    Connect Circuit: Follow the circuit diagram to set up the hardware.
    Press the Button: Every time you press the button, the LED will toggle between ON and OFF.

Installation & Setup
Step 1: Clone the Repository

Clone the repository to your local machine:

git clone https://github.com/YourUsername/LED_Button_Control.git

Step 2: Upload Code to Arduino

    Open the Arduino IDE.
    Copy the code from the repository (or open the .ino file in the IDE).
    Connect your Arduino to your computer using a USB cable.
    Select the correct board and port in the Arduino IDE.
    Click the "Upload" button to upload the code to the Arduino board.

Step 3: Build the Circuit

    Insert the 220Ω resistors and LEDs into the breadboard according to the diagram.
    Connect the LED anodes to pins 8 (for the LED) and the cathodes to GND.
    Insert the button and wire it to pin 5 on the Arduino and GND.
