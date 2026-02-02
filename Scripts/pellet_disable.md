This is a SCRIPT Blueprint. This provides a way to set an MQTT Topic to 1 or 0. Intended to supplement my [ThermoPI-Furnace](https://github.com/SirGoodenough/ThermoPI-Furnace) project.

## 📑 Changelog

* **2026-02-01**: First blueprint version 🎉

<base target="_blank"\>

## 🔮 About this blueprint

Type of blueprint: SCRIPT

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.md#contacts).

Why do I need this?

> This is a niche blueprint that was added to supplement my [ThermoPI-Furnace](https://github.com/SirGoodenough/ThermoPI-Furnace) project. One of the options there is to control a GPIO pit using MQTT. This Blueprint will be used to tuen that MQTT Topic on and on, allowing automation control ot the pin in Home Assistant.

#### 🗿License Notice:

* Copies of the original Blueprint that were converted via the 'Take Control' feature or other means are officially not supported by me.

* I may or may not be able to support you when you have a problem after you make changes to my code, as some of the code is no longer mine.

* I & my license also require attribution as a link back to the original should you use this code in your own creation.

* [Here is a link to my license & the original github post](https://github.com/SirGoodenough/HA_Blueprints?tab=License-1-ov-file) expected to be followed & referenced as attribution should you use this code elsewhere.

## 🔧 Configuration

Requirements

* [ThermoPI-Furnace](https://github.com/SirGoodenough/ThermoPI-Furnace) project up and running.
* You need to know the topic that that project is using to communicate toi MQTT. My default is this, yours should be similar:     ```homeassistant/binary_sensor/107935_pel_stove_disable/state```
* Suitable hardware connected to the selected GPIO pin to control. I'm using a small single relay module and the NC(normally closed) contacts are connected to my pellet feed. The reason is so that if the project is powered down, the pellet stove will work as originally intended. The pellet stove fuel feed will only be affected if the project is powered and the pin it enabled.

## <a name="fields">🗂 Field variables to feed variables from calling automation</a>

    control: name: Control State
        Set to 1 to shut off pellets, 0 to restore normal operation.
        required: false

## 🗂 Input fields

    mqtt_toggle_topic: name: BS Topic
        This is the MQTT Topic needed to change the Binary Sensor. It should look similar to:             ```homeassistant/binary_sensor/107935_pel_stove_disable/state```
        required: true

    state_default: name: Default state if no data is received when calling script
        Set this to 0 to default as off and 1 so default as on. This will assume 0 or off if not changed.
        required: false

## ✈️ Extended Information

For further information, reference these links below.

>     (https://github.com/SirGoodenough/ThermoPI-Furnace)

## 👀 Installation example

Once you have the entities created or decided upon you can build the Script.

To build the script:

[![Open your Home Assistant instance and show your blueprints.](https://my.home-assistant.io/badges/blueprints.svg)](https://my.home-assistant.io/redirect/blueprints/)

> 1. Click on 'Create Script' [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)  and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Find your MQTT Topic you need to control. I suggest MQTTExplorer would hemp you here. This topic is your only required input.
> 4. Call the script with data, '1' to turn the relay on, '0' to turn the relay off.

## 🥧 Example Usage

This is a case I use this in my setup. When my pellet stove internal temperature reached 500F for 5 minutes, it turns off the pellet feed. When it balls below 495 for 5 minutes, it turns the pellet feed back on.

    ```yaml
  `- id: '134082ab-6536-4074-82d2-173ebdba68fe'
    alias: Pellet Stove Limiter
    description: Stop feeding pellets when the stove is above 500 F
    triggers:
    - trigger: numeric_state
      entity_id:
      - sensor.furnace_pellet_firebox_temperature
      for:
        minutes: 5
      above: 500
      id: Hot
    - trigger: numeric_state
      entity_id:
      - sensor.furnace_pellet_firebox_temperature
      for:
        minutes: 5
      below: 490
      id: Cold
    - trigger: homeassistant
      event: start
      id: HA Start
    - trigger: homeassistant
      event: shutdown
      id: HA Stop
    conditions: []
    actions:
    - choose:
      - conditions:
        - condition: trigger
          id:
          - Hot
        sequence:
        - alias: It is Hot so stop feeding fuel
          action: script.pellet_feed_enable
          data:
            control: true
      - conditions:
        - condition: trigger
          id:
          - Cold
        sequence:
        - alias: It is cold so back to normal
          action: script.pellet_feed_enable
          data:
            control: false
      default:
      - alias: Stop interfering if you do not know the state
        action: script.pellet_feed_enable
        data:
          control: false
`  mode: single
    ```

This is what the script content for the Blueprint looks like in mine:

    ```yaml
    pellet_feed_enable:
    use_blueprint:
        path: SirGoodenough/pellet_disable.yaml
        input:
        mqtt_toggle_topic: homeassistant/binary_sensor/107935_pel_stove_disable/state
    alias: Pellet Feed Enable
    description: 'data: true to stop pellet feed and data: false to allow normal operation'
    icon: mdi:toggle-switch-off-outline
    ```

## 🌞 ❄️ Troubleshooting tip

If you are troubleshooting and you want to see more traces back when doing so, here is a TIP I've found.
Manually edit the automation created with the ui editor (or manually with a text editor) and add the following to have this automation contain 10 traces instead of the normal 5. Then if the automation is triggering often, you can see the last 10 traces to help you decide what the issue is.
[HA Docs on this here.](https://www.home-assistant.io/docs/automation/troubleshooting/#traces)

    ```yaml
    trace:
    stored_traces: 10
    ```

## 📩 **Version Updates**

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

📩 There is not an official version control system for Blueprints. However I have found something that comes pretty close. It is not perfect, but for **MOST** Blueprints, it does just fine. I encourage you to check this script out and use it to easily check if I have updated this blueprint. [🔗koter84 Blueprint Update Script ](https://github.com/koter84/HomeAssistant_Blueprints_Update/)

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fpellet_disable.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/pellet_disable.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/pellet_disable.yaml

# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md```

## <a name="contacts">🤹🏾‍♂️ Contact Links or see my other work</a>

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough