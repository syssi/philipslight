# Xiaomi Philips Light
Xiaomi Philips Lights integration for Home Assistant

The component allows you to control the state of your Xiaomi Philips LED Ball Lamp, Xiaomi Philips LED Ceiling Lamp and Xiaomi Philips Eyecare Smart Lamp 2

Thanks to [Rytilahti](https://github.com/rytilahti/python-mirobo) for all the work.

Please follow the instructions on [Retrieving the Access Token](https://home-assistant.io/components/xiaomi/#retrieving-the-access-token) to get the API token to use in the configuration.yaml file.

## Features
* On, Off
* Brightness
* Color temperature
* Attributes
  - power
  - model
  - brightness
  - color_temperature

## Setup

```
# confugration.yaml

light:
  - platform: xiaomi_philipslight
    name: Xiaomi Philips Smart LED Ball
    host: 192.168.130.67
    token: da548d86f55996413d82eea94279d2ff
  - platform: xiaomi_philipslight
    name: Xiaomi Philips Smart LED Ceiling Lamp
    host: 192.168.130.68
    token: 439e1a89ee5648d20482afa7839ef2ee
```

## Platform services

#### Service fan/xiaomi_miio_set_scene

Set one of the 4 available fixed scenes.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on specific light. Else targets all.         |
| `scene`                   |       no | Scene, between 1 and 4.                               |
