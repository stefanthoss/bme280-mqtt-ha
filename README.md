# bme280-mqtt-ha

Daemon for BME280 sensor reporting through MQTT to Home Assistant

This code uses the [Pimoroni bme280-python](https://github.com/pimoroni/bme280-python) code to scan the BME280 sensor attached to a raspberry pi and report the results over MQTT.

The daemon uses configparser() to read an .ini style file to get information on the MQTT server to contact.
It is also possible to set the i2c address for the sensor, and provide measurement offsets.
If elevation is provided (in meters), a sealevel pressure value is calculated and provided in the MQTT feed.

I am currently running this code on a raspberry pi zero W.

A systemd service file is also included and is part of the install process in the Makefile.

## Requirements

You can install these using:

```shell
sudo poetry install
```

Install the requirements in the `root` enviroment, or whichever enviroment make sense for you. Currently I run the daemon as root for easy access to /dev/i2c

## Home Assistant

When the MQTT integration is added to Home Assistant, the sensors will be added automatically through [MQTT Discovery](https://www.home-assistant.io/integrations/mqtt#mqtt-discovery). The prefix for the discovery topic (default `homeassistant`, see this repo's config file) can be changed.
