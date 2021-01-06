# Xiaomi Philips Lights

The component allows you to control the state of your Xiaomi Philips LED Ball Lamp, Xiaomi Philips LED Ceiling Lamp and Xiaomi Philips Eyecare Smart Lamp 2.

Thanks to [Rytilahti](https://github.com/rytilahti/python-mirobo) for all the work.

Please follow the instructions on [Retrieving the Access Token](https://home-assistant.io/components/xiaomi/#retrieving-the-access-token) to get the API token to use in the configuration.yaml file.

## Supported devices

| Name                             | Model                   | Model no.   | Specs |
| -------------------------------- | ----------------------- | ----------- | ----- |
| Philips Smart LED Ball           | `philips.light.bulb`      | 9290012800  | E27, 450lm, 3000K-5700K, 6.5W (12x0.37W / LED)  |
| Philips Smart LED Ceiling Lamp   | `philips.light.ceiling`   |             | |
| Philips EyeCare Smart Lamp       | `philips.light.sread1`    |             | ESP8266 version  |
| Philips EyeCare Smart Lamp Gen2  | `philips.light.sread2`    |             | ESP32 version  |
| Philips Moonlight Bedside Lamp   | `philips.light.moonlight` |             | |
| Philips LED Ceiling Light 620mm  | `philips.light.zyceiling` |             | |
| Philips Zhirui Smart LED Bulb E14 Candle Lamp  | `philips.light.candle`    | 9290018615  | **scrub**, E14, 200lm, 3000K-5700K, 4x0.25W CW + 4x0.25W WW / LED  |
| Philips Zhirui Smart LED Bulb E14 Candle Lamp  | `philips.light.candle2`   |             | **crystal**, E14, 200lm, 3000K-5700K, 4x0.25W CW + 4x0.25W WW / LED  |
| Philips Zhirui Desk Lamp         | `philips.light.mono1`     |             | |
| Philips Zhirui Downlight         | `philips.light.downlight` |             | |

## Features

### Philips LED Ball Lamp

* Power (on, off)
* Brightness
* Color temperature (175...333 mireds)
* Scene (1, 2, 3, 4)
* Delayed turn off (Resolution in seconds)
* Attributes
  - model
  - scene
  - delayed_turn_off

### Philips LED Ceiling Lamp

* Power (on, off)
* Brightness
* Color temperature (370-175 mireds / 2700K-5700K)
* Scene (1, 2, 3, 4)
* Night light mode (on, off)
* Delayed turn off (Resolution in seconds)
* Attributes
  - model
  - scene
  - delayed_turn_off
  - night_light_mode
  - automatic_color_temperature

### Philips Eyecare Smart Lamp 2

* Eyecare light (on, off)
* Ambient light (on, off)
* Brightness (of each light)
* Scene (1, 2, 3, 4)
* Night light mode (on, off)
* Delayed turn off (Resolution in seconds)
* Eye fatigue reminder / notification (on, off)
* Eyecare mode (on, off)
* Attributes
  - model
  - scene
  - delayed_turn_off
  - night_light_mode
  - reminder
  - eyecare_mode

### Philips Moonlight Bedside Lamp

* Power (on, off)
* Brightness
* Color
* Color temperature (588-153 mireds / 1700K-6500K)
* Scene (1, 2, 3, 4)
* Attributes
  - model
  - scene
  - sleep_assistant
  - sleep_off_time
  - total_assistant_sleep_time
  - brand_sleep
  - brand

## Install

You can install this custom component by adding this repository ([https://github.com/syssi/philipslight](https://github.com/syssi/philipslight/)) to [HACS](https://hacs.xyz/) in the settings menu of HACS first. You will find the custom component in the integration menu afterwards, look for 'Xiaomi Philips Lights Integration'. Alternatively, you can install it manually by copying the custom_component folder to your Home Assistant configuration folder.

## Setup

```
# configuration.yaml

light:
  - platform: xiaomi_miio_philipslight
    name: Xiaomi Philips Smart LED Ball
    host: 192.168.130.67
    token: da548d86f55996413d82eea94279d2ff
    model: philips.light.bulb
  - platform: xiaomi_miio_philipslight
    name: Xiaomi Philips Smart LED Ceiling Lamp
    host: 192.168.130.68
    token: 439e1a89ee5648d20482afa7839ef2ee
    model: philips.light.ceiling
  - platform: xiaomi_miio_philipslight
    name: Xiaomi Philips EyeCare Smart Lamp 2
    host: 192.168.130.69
    token: e8b19da37825a3056e84c522f05efce0
    model: philips.light.sread1
```

Configuration variables:
- **host** (*Required*): The IP of your light.
- **token** (*Required*): The API token of your light.
- **name** (*Optional*): The name of your light.
- **model** (*Optional*): The model of your light. Valid values are `philips.light.sread1`, `philips.light.ceiling`, `philips.light.zyceiling`, `philips.light.moonlight`, `philips.light.bulb`, `philips.light.candle`, `philips.light.candle2`, `philips.light.mono1` and `philips.light.downlight`. This setting can be used to bypass the device model detection and is recommended if your device isn't always available.

## Debugging

If the custom component doesn't work out of the box for your device please update your configuration to increase the log level:

```
logger:
  default: warn
  logs:
    custom_components.xiaomi_miio_philipslight: debug
    miio: debug
```

## Platform services

#### Service `xiaomi_miio_philipslight.light_set_scene`

Set one of the 4 available fixed scenes.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |
| `scene`                   |       no | Scene, between 1 and 4.                               |

#### Service `xiaomi_miio_philipslight.light_set_delayed_turn_off`

Delayed turn off.

| Service data attribute    | Optional | Description                                                                      |
|---------------------------|----------|----------------------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.                                  |
| `time_period`             |       no | Time period for the delayed turn off. Valid values are 5, '0:05', {'minutes': 5} |

#### Service `xiaomi_miio_philipslight.light_reminder_on` (Eyecare Smart Lamp 2 only)

Enable the eye fatigue reminder/notification.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `xiaomi_miio_philipslight.light_reminder_off` (Eyecare Smart Lamp 2 only)

Disable the eye fatigue reminder/notification.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `xiaomi_miio_philipslight.light_night_light_mode_on` (Eyecare Smart Lamp 2 only)

Turn the smart night light mode on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `xiaomi_miio_philipslight.light_night_light_mode_off` (Eyecare Smart Lamp 2 only)

Turn the smart night light mode off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `xiaomi_miio_philipslight.light_eyecare_mode_on` (Eyecare Smart Lamp 2 only)

Turn the eyecare mode on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `xiaomi_miio_philipslight.light_eyecare_mode_off` (Eyecare Smart Lamp 2 only)

Turn the eyecare mode off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |
