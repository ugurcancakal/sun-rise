
### Project Title: Raspberry Pi Sunrise Alarm System

---

### Overview

This project involves creating a sunrise simulation wake-up alarm using a Raspberry Pi and a dimmable LED bulb. The system gradually increases the brightness of the bulb in the morning, mimicking a natural sunrise to help you wake up more gently. The setup uses 220V AC power supply and safely interfaces it with the low-voltage Raspberry Pi using a TRIAC-based dimming circuit.

### Features

* **Smooth Sunrise Simulation** : Gradual increase in light intensity over a set period to simulate sunrise.
* **PWM Control** : The Raspberry Pi generates a PWM signal to control the dimmable LED bulb's brightness.
* **Safe High-Voltage Handling** : The circuit includes a TRIAC and optocoupler to safely control the 220V AC bulb.

### Component List

1. **Raspberry Pi** (any model with GPIO pins)
2. **Dimmable LED Bulb** (compatible with 220V AC and PWM dimming)
3. **TRIAC** (e.g., BTA16, suitable for 220V AC)
4. **Optocoupler** (e.g., MOC3021, for TRIAC triggering)
5. **Snubber Circuit Components** :
   1. Resistor (e.g., 330 ohms, 1W)
   2. Capacitor (e.g., 0.01µF, 600V)
6. **Resistor** (1k ohm, for current limiting in the optocoupler input)
7. **Heat Sink** (for the TRIAC, to dissipate heat)
8. **Breadboard and Jumper Wires** (for prototyping)
9. **220V AC Power Socket**
10. **5V USB Power Adapter** (for powering the Raspberry Pi)
11. **Insulated Enclosure** (for housing the high-voltage components safely)

### Circuit Overview

1. **AC Power Input** : Connects to 220V AC socket.
2. **TRIAC and Optocoupler** : The TRIAC controls the bulb's power, triggered by the optocoupler, which is driven by the Raspberry Pi's GPIO PWM output.
3. **Snubber Circuit** : Connected across the TRIAC to suppress voltage spikes and protect the circuit.
4. **Raspberry Pi** : Generates the PWM signal to control the bulb's brightness.

### Software Setup

**Python Script** : The script controls the PWM signal to simulate the sunrise.

1. **Start PWM** at a low duty cycle.
2. **Gradually Increase** the duty cycle over the configured time to simulate a sunrise.
3. **Schedule the Script** to run at the desired wake-up time using cron jobs.

### Safety Considerations

* **High Voltage Caution** : Exercise extreme caution when working with 230V AC. Ensure all connections are secure and insulated.
* **Enclosure** : Use a proper enclosure to prevent accidental contact with high-voltage components.
* **Heat Management** : Ensure the TRIAC has adequate heat sinking to prevent overheating.

### Installation & Setup

1. **Circuit Assembly** : Assemble the circuit on a breadboard first, then transfer to a PCB or permanent board once tested.
2. **Script Deployment** : Deploy the Python script on the Raspberry Pi, and test the PWM control.
3. **Cron Job Setup** : Use `crontab -e` to schedule the script to run at your desired wake-up time.

### Example Cron Job

To run the sunrise simulation at 7:00 AM every day:

```bash
0 7 * * * /usr/bin/python3 /home/pi/sunrise_simulation.py
```

### License

This project is licensed under the MIT License - see the [LICENSE]() file for details.
