# 🌐 This my Home Assistant Blueprint Library

This is the Home Assistant Blueprint Library I have created and am sharing with the community.  I have both Script and Automation Blueprints in separate folders.  Each Blueprint has a file with the .yaml suffix with all the code and a file with the .md suffix which is a markdown description for set-up and usage of the blueprint.  The .md file contains important information and if you want a successful install, you should read it.

## ⚙ Want to request a new feature request or found a BUG?

[Open an issue on GitHub](https://github.com/SirGoodenough/HA_Blueprints/issues/new/choose).

## 🫴 Support

You can use the threads on the Home Assistant community for the blueprint you are interested in (links below) to ask any questions you have.  

Also pop in there and say Thanks if you like my stuff!

Or join me on (Sir_Goodenough#9683) Discord [Discord Server WhatAreWeFixingToday](https://discord.gg/3HaKN8UJgn).

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

YouTube Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

## 🧀 If you want to support me

Buy me a Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday  #SirGoodEnough

Here is a list of each of my blueprints, a quick description, an import link for import to Home Assistant, and jump links to the Blueprints Exchange post and the files in my GIT Repo...

## 🌀 Scripts

#### 🧯Broadlink on Script Blueprint

This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, IE: antenna, FireTV, Chromecast, etc.  The defaults are specific to me and you should change them to match your situation.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FBroadlink_ON_script.yaml)

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

The scripts built with this Blueprint gives you a common scenario for turning your stuff on and putting the device in the correct mode to do the things you want to do.  I have a number instances of this blueprint script created in my system.  Here is a shot of them:

* [Broadlink_ON_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.md)
* [Broadlink_ON_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml)

#### 🧯Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FTasmota_EZ-Buttons.yaml)

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

* 1) Restart all your Tasmota devices
* 2) Upgrade Selected Tasmota Devices (optional)
* 3) Upgrade all your Tasmota Devices

* [Tasmota_EZ-Buttons.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.md)
* [Tasmota_EZ-Buttons.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml)

#### 🧯Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fplay_media_file_script.yaml)

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

 I decided I wanted to clean up a bunch of my automations by removing the several lines of YAML every time I wanted to play an mp3 file.  In addition to that, playing specific sound files and other things becomes a simple call to a script file, so really a function.  The actual meat and potatoes of the function is exactly the same for all the sounders and if a change needs to be made, it only has to be made in 1 place in a multiple re-use scenario.

* [play_media_file_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.md)
* [play_media_file_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.yaml)

#### 🧯TTS All Message Blueprint

This script can use any of the 11 integrated TTS Platforms in Home Assistant to send a message to a media player.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_All_Message_Script_Blueprint.yaml)

https://community.home-assistant.io/t/tts-script-blueprint-for-all-11-ha-core-tts-flavors/400700

_______________
> **NOTE:** This blueprint replaces 2 other blueprints, so those have been removed from the repository.  All the functionality in those has been moved to this one.
>
> * tts_cloud_message_script.yaml
>
> * tts_google_translate_say_message_script.yaml
>
_______________

* [tts_google_translate_say_message_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.md)
* [tts_google_translate_say_message_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.yaml)

#### 🧯Miscellaneous Blueprint Scripts designed to be called by other BP's for specific tasks

Color Control.  Designed for Magic Cube rotation input but can be used for anything.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fcolor_control_4_magic_cube.yaml)

Dimmer Control.  Designed for Magic Cube rotation input but can be used for anything.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fdimmer_control_4_magic_cube.yaml)

Long-short Toggle Control.  Designed for Magic Cube rotation input but can be used for anything.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Flong_short_toggle_4_magic_cube.yaml)

Volume Control.  Designed for Magic Cube rotation input but can be used for anything.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fvolume_control_4_magic_cube.yaml)

Device Reset. Turn something off, wait, then turn it back on.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fdevice_reset.yaml)

https://community.home-assistant.io/t/miscellaneous-blueprint-scripts-volume-dimming-reset-long-short-press-simulation-color-change/602059

* [Miscellaneous Blueprint Scripts - Volume - Dimming - Reset - Long Short Press Simulation - Color Change.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Miscellaneous%20Blueprint%20Scripts%20-%20Volume%20-%20Dimming%20-%20Reset%20-%20Long%20Short%20Press%20Simulation%20-%20Color%20Change.md)

## 🔃 Automations

#### 🧯Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan% control & MQTT fan control versions.

Click this badge to import this Blueprint.  This is the version that uses HA fan integration and 0%, 33%, 66%, & 100% values to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_HA_fan.yaml)

Click this badge to import this Blueprint.  This is the version that uses MQTT speeds 0, 1, 2, 3 to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_MQTT.yaml)

https://community.home-assistant.io/t/auto-fan-temp-control-for-3-speed-fan-using-ha-fan-or-mqtt-integration/326419

This functionality started as a way to help my Bedroom AC unit keep an even temperature throughout the bedroom over night.  My partner wanted the fan on, but not faster than it had to be.  I wanted it to change speeds following the temperature of the room.  So that's what I did.

* [AutoFanControl.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.md)
* [AutoFanControl HA_fan.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_HA_fan.yaml)
* [AutoFanControl_MQTT.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_MQTT.yaml)

#### 🧯Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fdoor_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

This blueprint is set up to watch a binary sensor.  When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice.  The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message.  The delay time and all the other parameters are adjustable.

* [door_open_tts_cloud_say_announcer_nabu_casa_required.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.md)
* [door_open_tts_cloud_say_announcer_nabu_casa_required.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

#### 🧯Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fkeypad_5_button_cipher_to_turn_on_something.yaml)

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

Think on this Blueprint as a lock from a common keypad, or a puzzle to solve in a safe house.  
ALSO you can watch the accompanying [YouTube Video](https://youtu.be/ZILTAZQPr_Q) about it here for detailed info!

* [keypad_5_button_cipher_to_turn_on_something.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.md)
* [keypad_5_button_cipher_to_turn_on_something.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml)

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller MQTT Triggred Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 100+ commands from the Xiaomi Magic Cube Remote.  

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml)

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing. NOTICE: Using this Blueprint, this cube *can* be triggered 74 ways, but only 38 of them are unique...

* [Zigbee2MQTT - Xiaomi Cube Controller MQTT Triggered.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.md)
* [Zigbee2MQTT - Xiaomi Cube Controller MQTT Triggered.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml)

#### 🧯ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller. 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.yaml)

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing.  

* [Zigbee2MQTT - ZemiSmart ZM-RM02 Controller.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.md)
* [Zigbee2MQTT - ZemiSmart ZM-RM02 Controller.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.yaml)

#### 🧯ZHA - Xiaomi Cube Controller Blueprint

This Blueprint uses a ZHA built sensor to sort out the 38 commands from the Xiaomi Magic Cube Remote.  

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/ZHA-Xiaomi_Cube_Controller.yaml)

https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/495975

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing. NOTICE: Using this Blueprint, this cube *can* be triggered many ways, but only 38 of them are unique...

* [Zigbee2MQTT - Xiaomi Cube Controller.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/ZHA-Xiaomi_Cube_Controller.md)
* [Zigbee2MQTT - Xiaomi Cube Controller.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/ZHA-Xiaomi_Cube_Controller.yaml)

#### 🧯Device_tracker Monitor & Notifier

This Blueprint monitors device_tracker entities that you choose & notifies you if they go offline  

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Device_tracker_Monitor_and_Notifier.yaml)

https://community.home-assistant.io/t/device-tracker-monitor-notifier/500688

It gives you the opportunity to devise an action to deal with it.  It started as a pfSense centered project but any device_tracker that has a state of home when it is running and something else when it is not available will work with this.

* [Device_tracker Monitor & Notifier.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Device_tracker_Monitor_and_Notifier.md)
* [Device_tracker Monitor & Notifier.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Device_tracker_Monitor_and_Notifier.yaml)

#### 🧯 Zigbee2MQTT Aqara Magic Cube T1-Pro CTP-R01 Xiaomi Lumi cagl02

This Blueprint gives you literally hundreds of actions available on the new Magic Cube.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.yaml)

https://community.home-assistant.io/t/zigbee2mqtt-aqara-magic-cube-t1-pro-ctp-r01-xiaomi-lumi-cagl02/525111

* [Zigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.md)
* [Zigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.yaml)

#### 🧯 Humidifier Water Throttle Control

This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water.  This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FHumidifierWaterThrottleControl.yaml)

https://community.home-assistant.io/t/humidifier-water-throttle-control/527583

* [HumidifierWaterThrottleControl.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.md)
* [HumidifierWaterThrottleControl.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml)

#### 🧯 Person_alert_Blueprint

This BluePrint will monitor a person or persons, and when they 'enter' or 'leave' the zone or zones you pick, it will trigger an action for both enter and leave phases. Yes, it will watch multiple people and multiple zones at the same time!

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FPerson_alert_Blueprint.yaml)

https://community.home-assistant.io/t/person-alert-blueprint/542209

* [Person_alert_Blueprint.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Person_alert_Blueprint.md)
* [Person_alert_Blueprint.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Person_alert_Blueprint.yaml)

#### 🧯 Octoprint_Additional_Buttons_Helper

This is Blueprint is provided as a helper for people using the Octoprint Plugin called OctoPrint-HomeAssistant. What this does is add 6 buttons, 4 of which you as the user can set your own G-Codes to for customizing. Also adds safe shutdown and presentation functions.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FOctoprint_Additional_Buttons_Helper.yaml)

https://community.home-assistant.io/t/octoprint-additional-buttons-helper-blueprint/549826

* [Octoprint_Additional_Buttons_Helper.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Octoprint_Additional_Buttons_Helper.md)
* [Octoprint_Additional_Buttons_Helper.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Octoprint_Additional_Buttons_Helper.yaml)
