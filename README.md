# philipslight
Xiaomi Philips Lights integration for Home Assistant

Thanks to [Rytilahti](https://github.com/rytilahti/python-mirobo) for all the work.

# Setup

```
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

# Features
* Basic functionality: on, off, current state, brightness and color temperature
