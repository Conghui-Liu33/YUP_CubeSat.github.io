# Chosing a Battery
## requirements
- Run time at least 30min
- Light weight/small size
- Connector type need to match pcb
- Safe

# Chosing a Regualtor
## requirements
- 3.3V output
- Calculated load's maximum current draw (must exceed __mA)

## BNO085 Sensor sampling rate choices
![Image](../Images/BNO085_1.png)
![Image](../Images/BNO085_2.png)
- Linear Acceleration (100Hz)
- Rotation Vector (100Hz)
- Gyrosope (100Hz)
- Accelerometer (100Hz)

Chose the same sampling rate (100Hz) for all BNO085 sensors to simplify data logging/anlysis and plotting.\

The BNO085 chip contains integrated sensor fusion, which internaly calculates the linear acceleration and rotation vectors and outputs those data. This is one of the main factor why I chose this chip.\

The current draw depends on sensor sampling rates and enviormental conditions.



