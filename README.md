# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython


 
## NAME:

## DEPARTMENT:

## ROLL NO:

## DATE OF EXPERIMENT:

## AIM

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY



FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
 ![image](https://github.com/user-attachments/assets/1c7234b9-5041-4156-94b8-0b846adb6b8e)
    Figure-01 circuit diagram of digital input interface 


Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython)
````
import dht
import machine 
import time

# Define DHT22 sensor pin (GPIO XX -15)
dht_pin = machine.Pin(15, machine.Pin.IN, machine.Pin.PULL_UP)
sensor = dht.DHT22(dht_pin)

while True:
    try:
        sensor.measure()
        temp = sensor.temperature() # Get temperature in Celsius 
        hum = sensor.humidity() # Get humidity
        print(f"Temperature: {temp:.1f}°C")
        print(f"Humidity: {hum:.1f}%")

    except Exception as e:
        print("Error reading sensor:", e)
    time.sleep(2) # Wait for 2 seconds before next reading


 
````
## OUTPUT
![Screenshot 2025-03-06 115251](https://github.com/user-attachments/assets/51e36a73-0892-46fe-99d5-6a05035197ee)



FIGURE-02: CIRCUIT CONNECTION

FIGURE-03: CODE EXECUTION OUTPUT

FIGURE-04: LED STATUS BASED ON SWITCH INPUTS
## TIMING DIGAGRAM 


UPLOAD YOUR TIMING DIGARAM HERE 



## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

