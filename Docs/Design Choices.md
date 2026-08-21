# Chosing a Battery
## requirements
- Run time at least 30min
- Light weight/small size
- Connector type need to match pcb
- Safe

Using a 3.7V Lipo battery means that voltage supply drops throughout discharge, ultimately would drop close to or below 3.3V. Thus, we need to use a buck-boost regualtor to get a stable 3.3V output.

# Chosing a Regualtor
## requirements
- 3.3V output
- Calculated load's maximum current draw (must exceed __mA)

![Image](../Images/Regulator_1.png)



## BNO085 Sensor sampling rate choices
![Image](../Images/BNO085_1.png)
![Image](../Images/BNO085_2.png)
- Linear Acceleration (100Hz)
- Rotation Vector (100Hz)
- Gyrosope (100Hz)
- Accelerometer (100Hz)

Choose the same report rate (100 Hz) for all selected BNO085 outputs to simplify data logging, analysis, and plotting.

The BNO085 chip contains integrated sensor fusion, which internaly calculates the linear acceleration and rotation vectors and outputs those data. This is one of the main factor why I chose this chip.

The current draw depends on sensor sampling rates and enviormental conditions.

## Calculations
Typical Current Estimate:
The BNO085 datasheet provides typical power consumption measurements for representative sensor configurations. The closest configuration to the intended operation is 6/9-axis sensor fusion at 100 Hz: 
VDDIO: 3.5 mA
VDD: 7.5 mA
Since both rails will be supplied by the 3.3 V regulator: I=3.5+7.5=11 mA
This is used as an estimated typical current, rather than an exact value.

A guaranteed maximum operating current for this specific configuration is not provided, so additional design margin will be included when sizing the power supply.
Estimation: 18 mA

## BME280 Power Consumption
![Image](../Images/BME280_1.png)
### Configuration
* Pressure: **50 Hz, ×4 oversampling**
* Temperature: **50 Hz, ×1 oversampling**
* Humidity: **1 Hz, ×1 oversampling**

### Average Current Calculation
![Image](../Images/BME280_2.png)

Measurement Time:
50 Hz → 1 / 50 = 20 ms per measurement

t_measure = 1.25 + 2.3(1) + [2.3(4) + 0.575]
          = 13.325 ms

Thus: 13.325 ms < 20 ms → 50 Hz works


**Pressure + Temperature @ 50 Hz**

```text
I(P+T) = (50 / 1000) × [205 + 350×(2×1) + 714×(2×4 + 0.5)]

       = 0.05 × [205 + 700 + 6069]

       = 348.7 µA
```

**Humidity @ 1 Hz**

```text
I(H) = (1 / 1000) × [340×(2×1 + 0.5)]

     = 0.001 × 850

     = 0.85 µA
```

**Total Average Current**

```text
IAVG = 348.7 + 0.85
     = 349.55 µA
     ≈ 0.350 mA
```

### Power Budget

* **Average current:** ~0.35 mA
* **Highest listed typical active current:** ~0.714 mA
* **Design allowance:** ~1 mA




