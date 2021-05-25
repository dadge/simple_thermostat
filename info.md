[![GitHub Release][releases-shield]][releases]
[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE)
[![hacs][hacsbadge]][hacs]
[![BuyMeCoffee][buymecoffeebadge]][buymecoffee]


_Component developed by using the amazing development template [blueprint][blueprint]._

This custom component for Home Assistant is an upgrade of the generic thermostat which handles presets mode in a very simple way.

## How Generic thermostat behaves with modes : 
Basically, the generic thermostat handle two preset mode : AWAY and NONE.
When AWAY mode is set, the thermostat will set the tempaerature with the away temperature defined in the yaml configuration. 
When NONE is selected, the temperature set is saved. Every time you set the mode as NONE, the temperature will be automatically set with the saved value. If you want to change the saved value, set the mode to NONE, set the deisred temperature, and that's it.

## How Simple Thermostat behaves with modes and additional feature
Define by default all the modes defined in the climate specs : https://developers.home-assistant.io/docs/core/entity/climate#presets
The simple thermostat reproduce the behavior of the mode NONE in generic thermostat and extend it to all the modes : 
* Pick a mode

![image](https://user-images.githubusercontent.com/1717155/119150574-dd6c2680-ba4e-11eb-80bb-a1164b0b9df4.png)

* Set a temperature

![image](https://user-images.githubusercontent.com/1717155/119150718-012f6c80-ba4f-11eb-9913-7c320bdce8cc.png)

* That's it ! The temperature is saved for this mode.
* Reproduce the previous step to update the temperatures / set other modes


## Minimum requirements

* This implementstion can override or superseed the core generic thermostat

## Installation

### HACS installation

1. Install [HACS](https://hacs.xyz/). That way you get updates automatically.
2. Add this Github repository as custom repository in HACS settings.
3. search and install "Simple Thermostat" in HACS and click `install`.
4. Modify your `configuration.yaml` as explain below.
5. Restart Home Assistant.

### Manual installation

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `simple_thermostat`.
4. Download _all_ the files from the `custom_components/simple_thermostat/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Modify your `configuration.yaml` as explain below
7. Restart Home Assistant

## Configuration

In the following examples we are assuming that you know how to configure a generic thermostat (if not please have a look at : https://www.home-assistant.io/integrations/generic_thermostat/ ) and we will just highlight the differences in the configuration to apply. 

```yaml
climate:
  - platform: simple_thermostat
    name: Study
    heater: switch.study_heater
    target_sensor: sensor.study_temperature
```

If you had already configure a generic thermostat the onli changes you have to do are the following : 
* platform must be changed from generic_thermostat to simple_thermostat
* away_temp must be removed

## Even Better with Scheduler Component ! 

In order to enjoy the full power of simple thermostat, I invite you to use it with https://github.com/nielsfaber/scheduler-component 
Indeed, the schdeuler component porpose a management of the climate base on the preset modes. This feature has limited interest with the generic thermostat but it becomes highly powerfull with Simple thermostat : 

Starting here, I assume you have installed Simple Thermostat and Scheduler Component.

In Scheduler, add a schedule : 

![image](https://user-images.githubusercontent.com/1717155/119146454-ee1a9d80-ba4a-11eb-80ae-3074c3511830.png)

Choose "climate" group, choose one (or multiple) entity/ies, select "MAKE SCHEME" and click next : 
(it is possible to choose "SET PRESET", but I prefer to use "MAKE SCHEME")

![image](https://user-images.githubusercontent.com/1717155/119147210-aa746380-ba4b-11eb-8def-479a741c0ba7.png)

Set your mode scheme and save : 

![image](https://user-images.githubusercontent.com/1717155/119147784-2f5f7d00-ba4c-11eb-9de4-5e62ff5e71a8.png)

In this example I set ECO mode during the night and the day when nobody's at home BOOST in the morning and COMFORT in the evening. 


I hope this example helps you, don't hesitate to give me your feedbacks !

## Contributions are welcome!

If you want to contribute to this please read the [Contribution guidelines](CONTRIBUTING.md)

***

[integration_blueprint]: https://github.com/custom-components/integration_blueprint
[simple_thermostat]: https://github.com/dadge/simple_thermostat
[buymecoffee]: https://www.buymeacoffee.com/dadge
[buymecoffeebadge]: https://img.shields.io/badge/Buy%20me%20a%20beer-%245-orange?style=for-the-badge&logo=buy-me-a-beer
[commits-shield]: https://img.shields.io/github/commit-activity/y/dadge/simple_thermostat.svg?style=for-the-badge
[commits]: https://github.com/dadge/simple_thermostat/commits/master
[hacs]: https://github.com/custom-components/hacs
[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[forum]: https://community.home-assistant.io/
[license-shield]: https://img.shields.io/github/license/dadge/simple_thermostat.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-Joakim%20Sørensen%20%40ludeeus-blue.svg?style=for-the-badge
[releases-shield]: https://img.shields.io/github/release/dadge/simple_thermostat.svg?style=for-the-badge
[releases]: https://github.com/dadge/simple_thermostat/releases
