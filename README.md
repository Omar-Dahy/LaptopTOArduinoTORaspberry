# Bidirectional Communication: Laptop ↔ Raspberry Pi ↔ ESP32

## Overview
This project demonstrates bidirectional communication between a **Laptop**, a **Raspberry Pi**, and an **ESP32**. The Laptop sends commands (such as "AA" or "BB") to the Raspberry Pi, which forwards them to the ESP32. The ESP32 performs actions (e.g., blinking an LED) based on the received command and sends feedback back to the Raspberry Pi, which is relayed to the Laptop.

## Components Used
- **Laptop**: Running a Python script to send and receive data.
- **Raspberry Pi**: Acts as an intermediary, forwarding commands from the Laptop to the ESP32.
- **ESP32 **: Receives commands, performs actions (e.g., blinking an LED), and sends feedback to the Raspberry Pi.
- **LED**: Attached to the ESP32, blinks based on the commands received.

## Setup Instructions

### Hardware Setup:
1. **Connect the ESP32 to the Raspberry Pi**:
   - Use a USB cable to connect the **ESP32** to the **Raspberry Pi**.

2. **Connect Raspberry Pi to Laptop**:
   - Use an Ethernet cable or Wi-Fi to connect the **Raspberry Pi** to the **Laptop**.

### Software Setup:
1. **Install Required Packages**:
   - Install Python on your **Laptop** and **Raspberry Pi** if not already installed.
   - Install the `pyserial` library on your **Laptop** and **Raspberry Pi** to handle serial communication:
     ```bash
     pip install pyserial
     ```

2. **Upload ESP32 Code**:
   - Open the `ESP32_code.ino` file in the **ESP32 IDE**.
   - Select your **ESP32 ** board and upload the code.

3. **Run Raspberry Pi Script**:
   - On the **Raspberry Pi**, run the `raspberry_pi_script.py` to listen for incoming commands from the Laptop and send them to the ESP32.
   - Ensure the script points to the correct serial port where your ESP32 is connected (`/dev/ttyUSB0` or `/dev/ttyACM0`).

4. **Run Laptop Script**:
   - On the **Laptop**, run the `laptop_script.py` to send commands to the **Raspberry Pi**.
   - The script will wait for your input (either "AA" or "BB").

## How It Works

1. **Laptop → Raspberry Pi**:
   - The Laptop sends a command (e.g., "AA" or "BB") to the Raspberry Pi using the Python script.

2. **Raspberry Pi → ESP32**:
   - The Raspberry Pi sends the received command to the ESP32 over the serial connection.

3. **ESP32**:
   - The ESP32 blinks an LED based on the command:
     - **"AA"**: Blinks the LED **5 times**.
     - **"BB"**: Blinks the LED **10 times**.
   - After completing the action, ESP32 sends a confirmation message (e.g., "LED blinked 5 times") back to the Raspberry Pi.

4. **Raspberry Pi → Laptop**:
   - The Raspberry Pi sends the feedback received from the ESP32 back to the Laptop.
   - The Laptop prints the feedback on the screen.

## Commands
- **"AA"**: Blink the LED **5 times**.
- **"BB"**: Blink the LED **10 times**.

The ESP32 responds with feedback like:
- **"LED blinked 5 times"**
- **"LED blinked 10 times"**

## Important Notes

- Ensure the correct serial port is specified in the Python script (`/dev/ttyUSB0` or `/dev/ttyACM0`).
- Make sure your **ESP32** is correctly connected to the **Raspberry Pi** and powered on.
- The **Raspberry Pi** needs to have the `pyserial` library installed to communicate over the serial port.

## Contributing
Feel free to fork this repository, contribute improvements, or submit pull requests.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements
- Special thanks to all open-source contributors and documentation that helped in setting up serial communication with Raspberry Pi and ESP32.
