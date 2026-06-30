# Engineering Log

---

## June 29, 2026

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
Configured the correct USB serial interface and verified communication with a simple test program before reconnecting the sensors.

### Lesson Learned
Programming, debugging, and serial communication are separate subsystems. Test them independently.
