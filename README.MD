# ASUS EX-B650M-V7 Motherboard NCT-6799D Linux lm-sensor Configuration

This configuration file is designed for the **ASUS EX-B650M-V7** motherboard using the **NCT-6799D** sensor chip. It provides accurate monitoring of system voltages, fan speeds, and temperatures. The configuration is intended for use with **Linux systems** to monitor system health and ensure safe operating conditions.

## Configuration Overview

This configuration defines the voltage, fan, and temperature sensor readings for the **NCT-6799D** sensor on the **ASUS EX-B650M-V7** motherboard. Key values for each sensor, including voltage ranges, fan speeds, and temperature thresholds, are set to provide real-time monitoring.

## Configuration File Location

The configuration file should be placed in the `/etc/sensors.d/` directory as `nct6799.conf`.

```bash
sudo cp nct6799.conf /etc/sensors.d/
```

## Voltage Sensor Calibration

The following voltage sensors have been calibrated with the expected voltage ranges:

- **VCore**:  
  - Min: 0.75V  
  - Max: 1.5V  

- **AVSB**:  
  - Min: 3.1V  
  - Max: 3.5V  

- **3VCC**:  
  - Min: 3.1V  
  - Max: 3.5V  

- **12V**:  
  - Min: 11.4V  
  - Max: 12.6V  
  - Computed with factor `11.98`

- **5V**:  
  - Min: 4.8V  
  - Max: 5.2V  
  - Computed with factor `5`

- **3VSB**:  
  - Min: 3.1V  
  - Max: 3.5V  

- **VBAT**:  
  - Min: 3.0V  
  - Max: 3.3V  

- **VTT**:  
  - Min: 3.1V  
  - Max: 3.5V  

## Fan Speed Labels

Fan labels have been set for the following fan headers:

- **Fan 1**: Chasis 1 Fan Speed  
- **Fan 2**: CPU Fan Speed  
- **Fan 3**: Chasis 2 Fan Speed  
- **Fan 4**: Chasis 3 Fan Speed  

### Minimum Fan RPM

The minimum RPM values for all fans have been set to `0` to allow for accurate monitoring, including when the fan speed is low or idle.

```bash
set fan1_min 0
set fan2_min 0
set fan3_min 0
set fan4_min 0
```

## Temperature Sensor Configuration

The temperature sensors have been set with the following labels and thresholds:

- **Motherboard (temp1)**:  
  - Max: 85°C  
  - Critical: 100°C  

- **CPU Package (temp2)**:  
  - Max: 90°C  
  - Critical: 95°C  

- **CPU (temp8)**:  
  - Max: 90°C  
  - Critical: 95°C  

- **TSIO (CPU) (temp13)**  

### Ignored Temperature Sensors

The following temperature sensors are ignored, as they may show incorrect values or are not relevant to system monitoring:

- AUXTIN0 to AUXTIN5
- PCH sensors (temp9, temp10, temp11, temp12)

## Installation Instructions

1. Copy the configuration file to the appropriate directory:

    ```bash
    sudo cp nct6799.conf /etc/sensors.d/
    ```

2. Run **sensors-detect** to ensure the NCT-6799D chipset is recognized:

    ```bash
    sudo sensors-detect
    ```

3. Once detected, load the **nct6775** kernel module using the following command:

    ```bash
    sudo modprobe nct6775
    ```

4. After loading the module, run the following command to check if sensor readings are active:

    ```bash
    sensors
    ```

If everything is configured correctly, you should see real-time voltage, fan speed, and temperature readings in the output.

## Conclusion

This configuration provides detailed monitoring for the **ASUS EX-B650M-V7** motherboard with the **NCT-6799D** chipset. By following the steps outlined in this README, you can easily configure and monitor your system’s health under Linux.

For more information, visit the official [NCT-6775 Kernel Driver documentation](https://docs.kernel.org/hwmon/nct6775.html) or refer to the [LM-Sensors](https://linux.die.net/man/1/sensors) project for detailed sensor support.

--- 

This README file provides an overview and installation instructions for the **nct6799.conf** configuration. It includes the correct voltage, fan, and temperature settings to monitor system health effectively on the **ASUS EX-B650M-V7** motherboard with the **NCT-6799D** chipset.

