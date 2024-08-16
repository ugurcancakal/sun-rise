### Project Title: Raspberry Pi Sunrise Alarm System

### Overview

This project involves creating a sunrise simulation wake-up alarm using a Raspberry Pi and a dimmable LED bulb. The system gradually increases the brightness of the bulb in the morning, mimicking a natural sunrise to help you wake up more gently. The setup uses 230V AC power supply and safely interfaces it with the low-voltage Raspberry Pi using a TRIAC-based dimming circuit. A separate 5V power supply from the mains powers the entire circuit, including the ESP32 for PWM control. An 85°C thermal fuse is included for critical overheating protection.

### Features

* **Smooth Sunrise Simulation** : Gradual increase in light intensity over a set period to simulate sunrise.
* **PWM Control** : The ESP32 generates a PWM signal to control the dimmable LED bulb's brightness.
* **Thermal Protection** : An 85°C thermal fuse cuts power if the TRIAC overheats, ensuring the circuit's safety.
* **Integrated Power Supply** : The entire circuit is powered from a 230V AC source, using a 5V AC-DC converter.

### Component List

1. **Raspberry Pi** (any model with GPIO pins) - Optional if used as the server only.
2. **ESP32** : For generating the PWM signal and wireless communication with the Raspberry Pi.
3. **Dimmable LED Bulb** (compatible with 230V AC and PWM dimming)
4. **TRIAC** (e.g., BTA16, suitable for 230V AC)
5. **Optocoupler** (e.g., MOC3021, for TRIAC triggering)
6. **Snubber Circuit Components** :

* Resistor (330 ohms, 1W)
* Capacitor (0.01µF, 600V)

1. **5V AC-DC Power Supply Module** (5V 5W) to power the ESP32 and control circuit.
2. **Thermal Fuse** (85°C) to protect against overheating.
3. **Heat Sink** for the TRIAC.
4. **Capacitors** : 10µF electrolytic capacitors for power supply stabilization.
5. **Resistors** : 1kΩ for current limiting in the optocoupler input.
6. **Insulated Enclosure** : For housing the high-voltage components safely.

### Circuit Overview

#### A. **AC-DC Power Supply Section**

* **Input** : 230V AC from the wall socket.
* **Output** : 5V DC, used to power both the ESP32 and the TRIAC control circuitry.

#### B. **TRIAC Dimming Circuit**

* **PWM Output from ESP32** : Drives the input of the optocoupler.
* **Optocoupler Output** : Controls the gate of the TRIAC.
* **TRIAC** : Modulates the power to the dimmable LED bulb based on the PWM signal.
* **Snubber Circuit** : Protects the TRIAC from voltage spikes.

#### C. **Thermal Protection**

* **85°C Thermal Fuse** : Placed near the TRIAC to cut off power if overheating occurs. This protects the circuit from potential thermal damage.

### Safety Considerations

* **Thermal Fuse** : The 85°C thermal fuse provides critical protection against overheating, particularly for the TRIAC. This prevents potential damage or fire hazards due to excessive heat.
* **Insulated Enclosure** : Ensure all high-voltage components are securely housed to prevent accidental contact and electrical shocks.
* **Heat Management** : The TRIAC is equipped with a heat sink to dissipate heat effectively.

### Installation & Setup

1. **Circuit Assembly** : Assemble the circuit on a PCB, ensuring proper spacing and insulation between high-voltage AC and low-voltage DC components.
2. **Power Supply** : Connect the 230V AC input to the 5V AC-DC converter. Verify the 5V output before connecting it to the ESP32 and the control circuit.
3. **Thermal Fuse Placement** : Install the 85°C thermal fuse close to the TRIAC, ensuring it will trip if the TRIAC overheats.

### Example Cron Job for Sunrise Simulation

To run the sunrise simulation at 7:00 AM every day:

```bash
0 7 * * * /usr/bin/python3 /home/pi/sunrise_simulation.py
```

### License

This project is licensed under the MIT License - see the [LICENSE]() file for details
