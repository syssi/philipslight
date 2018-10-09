# Xiaomi Philips Lights

The component allows you to control the state of your Xiaomi Philips LED Ball Lamp, Xiaomi Philips LED Ceiling Lamp and Xiaomi Philips Eyecare Smart Lamp 2.

Thanks to [Rytilahti](https://github.com/rytilahti/python-mirobo) for all the work.

Please follow the instructions on [Retrieving the Access Token](https://home-assistant.io/components/xiaomi/#retrieving-the-access-token) to get the API token to use in the configuration.yaml file.

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
* Color temperature (588-153 mireds / 1700K-6500K)

## Setup

```
# configuration.yaml

light:
  - platform: xiaomi_miio
    name: Xiaomi Philips Smart LED Ball
    host: 192.168.130.67
    token: da548d86f55996413d82eea94279d2ff
    model: philips.light.bulb
  - platform: xiaomi_miio
    name: Xiaomi Philips Smart LED Ceiling Lamp
    host: 192.168.130.68
    token: 439e1a89ee5648d20482afa7839ef2ee
    model: philips.light.ceiling
  - platform: xiaomi_miio
    name: Xiaomi Philips EyeCare Smart Lamp 2
    host: 192.168.130.69
    token: e8b19da37825a3056e84c522f05efce0
    model: philips.light.sread1
```

Configuration variables:
- **host** (*Required*): The IP of your light.
- **token** (*Required*): The API token of your light.
- **name** (*Optional*): The name of your light.
- **model** (*Optional*): The model of your light. Valid values are `philips.light.bulb`, `philips.light.sread1` and `philips.light.ceiling`. This setting can be used to bypass the device model detection and is recommended if your device isn't always available.

## Platform services

#### Service `light.xiaomi_miio_set_scene`

Set one of the 4 available fixed scenes.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |
| `scene`                   |       no | Scene, between 1 and 4.                               |

#### Service `light.xiaomi_miio_set_delayed_turn_off`

Delayed turn off.

| Service data attribute    | Optional | Description                                                                      |
|---------------------------|----------|----------------------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.                                  |
| `time_period`             |       no | Time period for the delayed turn off. Valid values are 5, '0:05', {'minutes': 5} |

#### Service `light.xiaomi_miio_reminder_on` (Eyecare Smart Lamp 2 only)

Enable the eye fatigue reminder/notification.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `light.xiaomi_miio_reminder_off` (Eyecare Smart Lamp 2 only)

Disable the eye fatigue reminder/notification.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `light.xiaomi_miio_night_light_mode_on` (Eyecare Smart Lamp 2 only)

Turn the smart night light mode on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `light.xiaomi_miio_night_light_mode_off` (Eyecare Smart Lamp 2 only)

Turn the smart night light mode off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `light.xiaomi_miio_eyecare_mode_on` (Eyecare Smart Lamp 2 only)

Turn the eyecare mode on.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |

#### Service `light.xiaomi_miio_eyecare_mode_off` (Eyecare Smart Lamp 2 only)

Turn the eyecare mode off.

| Service data attribute    | Optional | Description                                           |
|---------------------------|----------|-------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific light. Else targets all.       |
