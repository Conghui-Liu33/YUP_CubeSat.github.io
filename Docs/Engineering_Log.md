# Engineering Log

---

## June 15, 2026

### Problem
The STM32 uploaded successfully, but the Serial Monitor showed no output.

### Investigation
- Checked the COM port.
- Tested the USB cable.
- Verified `Serial.begin(115200)`.
- Ran a simple Blink sketch.

### Root Cause
The USB serial connection was not configured correctly.

### Solution
- Bought a ST-Link
- Configured the correct USB serial interface and verified communication with a simple test program before reconnecting the sensors.

### Lesson Learned
Programming, debugging, and serial communication are separate subsystems. Can test them independently.

---

## June 26, 2026

### Problem
When testing BNO085 position recognition (roll, pitch, yaw), the change in angle is inacurate. When turned 90 degrees, the serial output showed a 180 degrees change.

![Image](../Images/problem2.png)

### Investigation
- Serial output quaternion values to determine whether the angle conversion is wrong or something else.

### Root Cause
![Image](../Images/problem3.png)
- The rotation vector values and the accelerometer values match exactly. Meaning the quaternion is measured incorrectly.
- Were missing these two lines of code:
    // if (bno08x.getSensorEvent(&sensorValue))
    // if (sensorValue.sensorId == SH2_ACCELEROMETER)

### Solution
Added those lines of code, tested sensor with different output frequencies (10Hz, 5Hz).

### Lesson Learned
- BNO085 library requires to first determine if new data needs to be read, then see if it matches the data type you want.
- Each sensor can have their individual output time, which is an engineering decision to make.
