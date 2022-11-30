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

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday  #SirGoodEnough

Here is a list of each of my blueprints, a quick description, and an import link for import to home assistant, and jump links to the Blueprints Exchange post and the files in my GIT Repo...

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

## 🔃 Automations

#### 🧯Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan% control & MQTT fan control versions.

Click this badge to import this Blueprint.  This is the version that uses HA fan integration and 0%, 33%, 66%, & 100% values to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FAutoFanControl%2520HA_fan.yaml)

Click this badge to import this Blueprint.  This is the version that uses MQTT speeds 0, 1, 2, 3 to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FAutoFanControl_MQTT.yaml)

https://community.home-assistant.io/t/auto-fan-temp-control-for-3-speed-fan-using-ha-fan-or-mqtt-integration/326419

This functionality started as a way to help my Bedroom AC unit keep an even temperature throughout the bedroom over night.  My partner wanted the fan on, but not faster than it had to be.  I wanted it to change speeds following the temperature of the room.  So that's what I did.

* [AutoFanControl.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.md)
* [AutoFanControl HA_fan.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl%20HA_fan.yaml)
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

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38 commands from the Xiaomi Magic Cube Remote.  

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZigbee2MQTT%2520-%2520Xiaomi%2520Cube%2520Controller.yaml)

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing. NOTICE: Using this Blueprint, this cube *can* be triggered 74 ways, but only 38 of them are unique...

* [Zigbee2MQTT - Xiaomi Cube Controller.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.md)
* [Zigbee2MQTT - Xiaomi Cube Controller.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.yaml)

#### 🧯ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller. 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZigbee2MQTT%2520-%2520ZemiSmart%2520ZM-RM02%2520Controller.yaml)

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing.  

* [Zigbee2MQTT - ZemiSmart ZM-RM02 Controller.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20ZemiSmart%20ZM-RM02%20Controller.md)
* [Zigbee2MQTT - ZemiSmart ZM-RM02 Controller.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20ZemiSmart%20ZM-RM02%20Controller.yaml)

#### 🧯ZHA - Xiaomi Cube Controller Blueprint

This Blueprint uses a ZHA built sensor to sort out the 38 commands from the Xiaomi Magic Cube Remote.  

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZHA%2520-%2520Xiaomi%2520Cube%2520Controller.yaml)

https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/495975

The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do.  Functions that are left empty will simply do nothing. NOTICE: Using this Blueprint, this cube *can* be triggered many ways, but only 38 of them are unique...

* [Zigbee2MQTT - Xiaomi Cube Controller.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/ZHA%20-%20Xiaomi%20Cube%20Controller.md)
* [Zigbee2MQTT - Xiaomi Cube Controller.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/ZHA%20-%20Xiaomi%20Cube%20Controller.yaml)
