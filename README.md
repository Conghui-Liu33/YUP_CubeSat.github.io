# STM32 Avionics Board

## Project Overview

I'm designing a modular STM32 avionics board for small aerospace vehicles.

![Prototype](Images/breadboard.jpg)

## System Architecture

The system uses an STM32F411 as the main controller. It connects to an IMU, GPS, BME280 sensor, and SD card.

![System Architecture](Images/system_architecture.png)

## Hardware

Main components:
- STM32F411
- BNO085 IMU
- BME280 sensor
- M10 GPS
- MicroSD module

![Wiring](Images/stm32_wiring.jpg)

## Software

The firmware reads sensor data using I2C, UART, and SPI. It organizes the data with timestamps and logs it to a CSV file.

## PCB

This section will include my schematic, PCB layout, and design decisions.

![PCB Layout](Images/pcb_layout.png)

## Testing

Testing includes sensor bring-up, GPS testing, SD card logging, and full system validation.

![Testing Setup](Images/testing_setup.jpg)

## Results

This section will include flight data, graphs, and performance results.

![Results Graph](Images/results_graph.png)

## Future Improvements

Future improvements include a custom PCB revision, better power management, radio telemetry, and a stronger enclosure.
