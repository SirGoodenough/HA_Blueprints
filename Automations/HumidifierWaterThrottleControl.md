This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water.  This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

## 📑 Changelog

* **2023-01-30**: 🎉 First Release

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FHumidifierWaterThrottleControl.yaml)

Direct link to download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml

## 📩 * Version Updates

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

🔗 There is not an official version control system for Blueprints.  However I have found something that comes pretty close.  It is not perfect, but for **MOST** Blueprints, it does just fine.  I encourage you to check this script out and use it to easily check if I have updated this blueprint.

[koter84 Blueprint Update Script](https://gist.github.com/koter84/86790850aa63354bda56d041de31dc70#file-readme-md)

## 🔧 Configuration

Requirements

    Tasmota SV Device set-up to receive the output of this blueprint.
    Suitable Humidifier to control.
    Generic hygrostat integration or something similar.

## 🗂 Input fields

    humidifier ✯ REQUIRED ✯: This is the entity that represents the Generic hygrostat controlling the system.

    humidity ✯ REQUIRED ✯: This is the entity used by the blueprint and Generic hygrostat to monitor the living area.

    mqtt_topic ✯ REQUIRED ✯: A topic such as this with your device top topic. We are setting var2 via cmnd: "cmnd/humidifier/var2" 
                             See below for more details.

    minimum_time: Current default 20 seconds. Must be set lower than the maximum time. This it the shortest time that will be sent to the switch.

    maximum_time: Current default 80 seconds. Must be set higher than the minimum time. This it the longest time that will be sent to the switch. It is also used in the formula to calculate the time sent to the switch.

## 👀 Where is My MQTT Topic?

    The Blueprint needs to send the time value to var2 in your sonoff SV. On my system the MQTT topic to do this is cmnd/humidifier/var2.  Yours will be something similar. In order to determine exactly what your will be, follow these instructions.

    Begin by opening the webui of your Tasmota SV switch.

#### Select the Configuration tab

![Where is the Configuration TAB?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaConfig.jpg)

#### Select the MQTT tab

![Where is the Configure MQTT TAB?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaMQTT.jpg)

#### Bottom of the screen is the topic

![Where is the TOPIC?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaTopic.jpg)

## 🙊 How Do I Set-up My Sonoff SV?

#### Add a ghost relay and button as relay and button #2 in the Module Parameters screen & save it.

![Module Setup](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaModuleSetup.jpg)

#### Add the Rules

    Make sure you set all 3 rules to mode 4 after you oad them.
    Rule1 4
    Rule2 4
    Rule3 4

    Also make sure you turn on the 2 rules. Rule1 will turn on and off as called in the program.
    Rule2 1
    Rule3 1

    Full line of text versions of these rules are available in the Blueprint Description.  These are layed out for clarity.

Rule1 is turned on and off based on the status of Power2. When Rule1 is enabled it sets the 2 minute timer cycle and starts the Rule3 items on schedule.  It sets variable 1 to the value of variable 2.  Variable 2 is set via MQTT from the Blueprint.

```text
on Time#Minute|2 do var1 %var2% endon
```

Rule2 Provides set-up for boot and is the code for switching Rule1 on and off based on the status of Power2. Power1 is connected to the real relay and sends power to the water valve when on. Power2 (the ghost relay) is used by the Generic hygrostat to call for moisture or standby.

```text
on system#boot do backlog power2 0; var2 20 endon 
on POWER2#state=0 do backlog power1 0; rule1 0 endon 
on POWER2#state=1 do rule1 1 endon
```

Rule3 is the look-up table. It selects the delay time, which is the amount of time that the water cycles on within the 2 minute cycle based on the input on var2 from the blueprint. It has to be done this way because the Delay function in Tasmota does not accept a VARx value. Tasmota will test these from the top to the bottom and when it finds the first one that executes will end the line with a break and stop trying for more. It is a small footprint method of if/then coding. This table will allow water on times up to the full 120 seconds listed as a limit in the Blueprint.

```text
on var1#state>110 do backlog power1 on;delay 1200;power1 off break 
on var1#state>100 do backlog power1 on;delay 1100;power1 off break 
on var1#state>90 do backlog power1 on;delay 1000;power1 off break 
on var1#state>80 do backlog power1 on;delay 900;power1 off break 
on var1#state>70 do backlog power1 on;delay 800;power1 off break 
on var1#state>60 do backlog power1 on;delay 700;power1 off break 
on var1#state>50 do backlog power1 on;delay 600;power1 off break 
on var1#state>40 do backlog power1 on;delay 500;power1 off break 
on var1#state>30 do backlog power1 on;delay 400;power1 off break 
on var1#state>20 do backlog power1 on;delay 300;power1 off break 
on var1#state<=20 do backlog power1 on;delay 200;power1 off endon
```

# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

Here is a list of each of my blueprints, a quick description and jump links to the Blueprints Exchange post...

## 🌀 Scripts

#### 🧯Broadlink on Script Blueprint

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, Pushes remote buttons in sequence.

#### 🧯Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

#### 🧯Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean.

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

#### 🧯TTS All Message Blueprint

This script can use any of the 11 integrated TTS Platforms in Home Assistant to send a message to a media player.

https://community.home-assistant.io/t/tts-script-blueprint-for-all-11-ha-core-tts-flavors/400700

## 🔃 Automations

#### 🧯Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan % control & MQTT fan control versions.

https://community.home-assistant.io/t/auto-fan-temp-control-for-3-speed-fan-using-ha-fan-or-mqtt-integration/326419

#### 🧯Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### 🧯Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38(+54) commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

#### 🧯Zigbee2MQTT - ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller.

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

#### 🧯ZHA - Xiaomi Cube Controller Blueprint

This Blueprint uses a ZHA built sensor to sort out the 38(+54) commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zha-xiaomi-cube-controller/495975

#### 🧯Device_tracker Monitor & Notifier

This Blueprint Monitor's device_tracker entities that you choose & notifies you if they go offline. Then it gives you the opportunity to devise an action to deal with it.

https://community.home-assistant.io/t/device-tracker-monitor-notifier/500688

#### 🧯 Zigbee2MQTT Aqara Magic Cube T1-Pro CTP-R01 Xiaomi Lumi cagl02

This Blueprint gives you literally hundreds of actions available on the new Magic Cube.

https://community.home-assistant.io/t/zigbee2mqtt-aqara-magic-cube-t1-pro-ctp-r01-xiaomi-lumi-cagl02/525111

#### 🧯 Humidifier Water Throttle Control

This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water.  This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough