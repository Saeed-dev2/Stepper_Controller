# **Stepper Motor Control with Rotary Encoder and LCD Display**

This project demonstrates how to control a stepper motor using a rotary encoder for input and an I2C LCD for parameter display. It allows users to adjust degrees of rotation, RPM, dead time (DT), and direction, making it a flexible system for stepper motor applications.

## **Features**
- **User Input via Rotary Encoder:**
  - Adjust motor parameters: Degrees, RPM, Dead Time, and Direction.
  - Push button to switch between adjustable parameters.
- **LCD Display:**
  - Real-time display of motor parameters (`DEG`, `RPM`, `DT`, and Direction).
- **Stepper Motor Control:**
  - Move the motor forward and backward based on user-defined parameters.
  - Implements dead time delay between directional changes.
- **Interrupt for Emergency Stop:**
  - Allows the motor to stop immediately via an interrupt.


## **Hardware Requirements**
- Arduino (e.g., Uno, Mega, or Nano)
- Stepper Motor and Driver (e.g., A4988, DRV8825)
- Rotary Encoder (with push button)
- I2C LCD Display (16x2 or similar)
- Push Buttons (for `START`, `SWEN`)
- LEDs (for indicating motor/system states)
- Power Supply suitable for stepper motor driver

### **Pin Connections**
| Component            | Arduino Pin | Description                     |
|----------------------|-------------|---------------------------------|
| Rotary Encoder SW    | `2`         | Rotary encoder push button      |
| Rotary Encoder DT    | `4`         | Rotary encoder DT signal        |
| Rotary Encoder CLK   | `5`         | Rotary encoder CLK signal       |
| Stepper Driver PUL   | `6`         | Pulse signal for stepper driver |
| Stepper Driver DIR   | `7`         | Direction control               |
| Stepper Driver EN    | `8`         | Enable stepper motor driver     |
| LED (Motor Start)    | `9`         | Indicates motor is running      |
| LED (Motor Enabled)  | `13`        | Indicates motor driver enabled  |
| START Button         | `10`        | Starts the motor sequence       |
| SWEN Button          | `12`        | Enables/disables motor driver   |
| LCD SDA              | `A4`        | I2C SDA connection              |
| LCD SCL              | `A5`        | I2C SCL connection              |


## **Software Setup**

### **Libraries Required**
1. **Wire**: For I2C communication.
   - Preinstalled with Arduino IDE.
2. **LiquidCrystal_I2C**: For interfacing with the I2C LCD.
   - Install from Arduino Library Manager.

### **Code Configuration**
1. Download the code from this repository.
2. Adjust the `min` and `max` constraints for parameters (`minR`, `maxR`, etc.) as needed.
3. Upload the code to your Arduino board using the Arduino IDE.


## **How It Works**

1. **Initialization:**
   - Displays default values for parameters on the LCD.
   - System waits for the `START` button to be pressed.

2. **Setting Parameters:**
   - Use the rotary encoder to adjust:
     - Degrees (`DEG`) - Motor rotation.
     - RPM (`RPM`) - Speed of the motor.
     - Dead Time (`DT`) - Delay between directional changes.
     - Direction (`CW`/`CCW`).

3. **Starting the Motor:**
   - Press the `START` button to run the motor with current settings.
   - The motor rotates forward and backward for the specified degrees and speed.

4. **Stopping the Motor:**
   - Press the `SWEN` button to disable the motor driver.
   - An interrupt can also stop the motor immediately.


## **Usage**
### **Rotary Encoder Functionality**
- **Rotate Clockwise:** Increase the selected parameter.
- **Rotate Counterclockwise:** Decrease the selected parameter.
- **Press Encoder Button:** Switch between parameters (`DEG`, `RPM`, `DT`, `Direction`).

### **LCD Display**
| Parameter  | Description                  |
|------------|------------------------------|
| `DEG`      | Degrees of rotation          |
| `RPM`      | Rotational speed (RPM)       |
| `DT`       | Dead time (in seconds)       |
| `CW/CCW`   | Clockwise/Counterclockwise direction |


## **Future Improvements**
- **Debounce Logic:** Add software debounce for better rotary encoder performance.
- **Interrupt Handling:** Refactor ISR for safer operation.
- **Parameter Saving:** Implement EEPROM storage for persistent settings.
- **Improved UX:** Add more visual cues or sounds for parameter changes.

