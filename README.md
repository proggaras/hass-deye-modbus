# hass-deye-modbus
A simple way to directly integrate your Deye inverter into Home Assistant over Modbus. Additional addons are just used for a nice visualisation. 

## Overview
Below you will find my setup. Other Deye inverters or RS485 to Modbus converters can work as well.

![Label](/img/overview.drawio.svg)
* Deye 3 Phase Hybrid Inverter SUN-25K-SG01HP3-EU-AM2
* Waveshare RS485 TO POE ETH
* Home Assistant
  * Modbus Integration
  * Energy Dashboard
  * HACS
    * Power Flow Card Plus
    * Sunsynk-Power-Flow-Card

## Setup
### Deye Inverter 
### Modbus Converter
#### Update
To get my Waveshare davice working stable I had to update the Firmare to "V1.486".
To perform the Update follow this guide: https://github.com/alienatedsec/solis-ha-modbus-cloud/discussions/17
#### Configuration
Open the Webinterface of your device, set a static IP in your network and adapt the rest of configuration as displayed in the screenshot:
![Label](/img/waveshare_config.png)

### Home Assistant Modbus
Create a new file 'modbus.yaml':
```
  - name: Inverter1
    type: tcp
    host: "Ip of your Waveshare"
    port: "Port of your Waveshare
    delay: 3
    message_wait_milliseconds: 30
    retries: 3
    timeout: 5

    sensors:
    
      - name: "Deye Deye Heat sink temperature"
        slave: 1
        address: 541
        input_type: holding
        data_type: int16
        unit_of_measurement: "°C"
        scale: 0.1
        offset: -100
        precision: 2
...
```
# Sources:
A big Thank you to all of you for making this guide possible
* https://github.com/StephanJoubert/home_assistant_solarman
* 
* 
