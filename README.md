# esp-home-packages
This repo contains reuseable packages for ESP Home configurations. See also https://esphome.io/components/packages.html.

## Included Packages
- [Utils](#Utils): provides various diagnostics like uptime, mac adress, connection strength, etc.
- [INA219](#INA219): provides voltage and power sensors
- [BME680](#BME680): provides temperature, pressure, humidity and air quality sensors
- [BME680 - BSEC](#BME680-BSEC): provides temperature, pressure, humidity and air quality sensors using the Bosch BSEC library
- DF Robot CF4001: provides sensors and configuration parameters for the DF Robot CF4001 mmWave Radar Presence Sensor
- WS2812B: provides controls for a led strip
- HLK LD2410: provides sensors and configuration parameters for HLK LD2410 radar presence sensor
- VEML7700: provides an ambient light sensor
- PIR: provides an occupancy sensor for a PIR connected to an input pin
- Presence: provides a combines presence sensor based on a PIR and Radar sensor
- VELUX cover: provides a cover entity for controlling a Velux remote with ESP8266
- [APDS9960](#APDS9960): provides proximity and gesture sensors as well as a light level sensor

### Utils
#### Provides
- Uptime Sensor
- WiFi Signal (dB and %)
- Status
- IP Address
- Connected SSID
- Mac Address
- Last Restart
- Uptime

#### Requires
- None

### INA219
#### Provides
- Current
- Power
- Voltage
- Total Daily Energy
- Total Energy

#### Requires
- I2C Bus: "ina219_bus_id"

### BME680
#### Provides
- Temperature
- Pressure
- Humidity
- Gas Resistance
- Indoor Air Quality (IAQ)
- IAQ Classification

#### Requires
- I2C Bus: "bme_680_bus_id"

### BME680 - BSEC
> [!NOTE]
> The BSEC2 library is only available for use after accepting its software license agreement. By enabling this component in your configuration, you are explicitly agreeing to the terms of the [BSEC license agreement](https://www.bosch-sensortec.com/media/boschsensortec/downloads/software/bme688_development_software/2023_04/license_terms_bme688_bme680_bsec.pdf). Note that the license forbids distribution of any compiled firmware binaries that include this component.

#### Provides
- Temperature
- Pressure
- Humidity
- Gas Resistance
- Indoor Air Quality (IAQ)
- IAQ Classification
- IAQ Accuracy
- CO2 Equivalent
- Breath VOC Equivalent

#### Requires
- I2C Bus: "bme_680_bus_id"
- Temperature Offset: "bme680_temperature_offset"

### APDS9960
#### Provides
- Clear (Light Level)
- Proximity
- Up Movement (Gesture)
- Down Movement (Gesture)
- Left Movement (Gesture)
- Right Movement (Gesture)

#### Requires
- I2C Bus: "apds9960_bus_id"

## Example Useage
The following code snippet will add the Utils and WS2812B packages to a configuration when placed in the configuration.yaml of an ESP Home controlled device:

```yaml
substitutions:
  led_pin: "GPIO32"
  num_leds: "24"
  rgb_order: "GRB"

packages:
  remote_packages:
    url: https://github.com/mejand/esp-home-packages
    files: [utils.yaml, ws2812b_strip.yaml]
    ref: main
    refresh: 5s
```
