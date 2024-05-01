# light
// Define constants for the PIR sensor and LED
const int pirPin = 2;   // PIR sensor connected to digital pin 2
const int ledPin = 13;  // LED connected to digital pin 13

void setup() {
  pinMode(pirPin, INPUT);  // Set PIR sensor pin as input
  pinMode(ledPin, OUTPUT); // Set LED pin as output
  Serial.begin(9600);      // Initialize serial communication for debugging
}

void loop() {
  int pirState = digitalRead(pirPin); // Read the state of PIR sensor
  
  if (pirState == HIGH) {  // If motion is detected
    digitalWrite(ledPin, HIGH);  // Turn on the LED
    Serial.println("Motion detected!");
    delay(1000);  // Wait for 1 second
  } else {
    digitalWrite(ledPin, LOW);   // Turn off the LED
  }
}

//And here's a Python code for the same project using Raspberry Pi and the RPi.GPIO library:
import RPi.GPIO as GPIO
import time

# Define constants for the PIR sensor and LED
pir_pin = 17  # PIR sensor connected to GPIO pin 17
led_pin = 18  # LED connected to GPIO pin 18

# Set up GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setup(pir_pin, GPIO.IN)   # PIR sensor pin as input
GPIO.setup(led_pin, GPIO.OUT)  # LED pin as output

try:
    while True:
        pir_state = GPIO.input(pir_pin)  # Read the state of PIR sensor

        if pir_state == GPIO.HIGH:  # If motion is detected
            GPIO.output(led_pin, GPIO.HIGH)  # Turn on the LED
            print("Motion detected!")
            time.sleep(1)  # Wait for 1 second
        else:
            GPIO.output(led_pin, GPIO.LOW)  # Turn off the LED
finally:
    GPIO.cleanup()  # Clean up GPIO on exit

