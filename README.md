# Home Assitant Lights On at Sunset Appdaemon App

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)
<br><a href="https://www.buymeacoffee.com/Petro31" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-black.png" width="150px" height="35px" alt="Buy Me A Coffee" style="height: 35px !important;width: 150px !important;" ></a>

_Lights On at Sunset app for AppDaemon._

Simply toggles lights on at sundown, turns them off at sunrise.  You can set the light service data.

## Installation

Download the `sunset_lights` directory from inside the `apps` directory to your local `apps` directory, then add the configuration to enable the `hacs` module.

## Example App configuration

#### Simple switch
```yaml
sunsetlights:
  module: sunset_lights
  class: SunsetLights
  entities:
  - group.sconces
```

#### Advanced 
```yaml
sunsetlights:
  module: sunset_lights
  class: SunsetLights
  entities:
  - group.sconces
  - entity: light.office_lamp
    service_data:
      brightness: 100
      kelvin: 2700
  - entity: light.office_mood
    service_data:
      brightness: 130
      rgb_color: [255,0,0]
  log_level: INFO
```

#### App Configuration
key | optional | type | default | description
-- | -- | -- | -- | --
`module` | False | string | `sunset_lights` | The module name of the app.
`class` | False | string | `SunsetLights` | The name of the Class.
`entities`| False | list | | A list of entity_id's or entity objects.
`log_level` | True | `'INFO'` &#124; `'DEBUG'` | `'INFO'` | Switches log level.

#### Entity Object Configuration
key | optional | type | default | description
-- | -- | -- | -- | --
`entity` | False | string | | The entity_id of the switch or light.
`service_data` | True | map | | Turn on service data.  Whenever the door turns on a light or switch, this data will be passed to the service data.  Warning: Use only valid combinations.  Light combinations are not validated and can cause errors in Home Assistant.
