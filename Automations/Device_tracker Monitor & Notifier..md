This Blueprint Monitor's device_tracker entities that you choose & notifies you if they go offline. Then it gives you the opportunity to devise an action to deal with it.  It started as a pfSense centred project but and device_tracker that has a state of home when it is running and something else whei it is not available will work with this.

## 📑 Changelog

* **2022-12-10**: 🎉 First Released Version.

## 📩 * Version Updates

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

🔗 There is not an official version control system for Blueprints.  However I have found something that comes pretty close.  It is not perfect, but for **MOST** Blueprints, it does just fine.  I encourage you to check this script out and use it to easily check if I have updated this blueprint.

[koter84 Blueprint Update Script](https://gist.github.com/koter84/86790850aa63354bda56d041de31dc70#file-readme-md)

### Option 1: My Home Assistant

Click the link below to import this Blueprint: 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fdoor_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

# Please Click the 🧡 at the end of the Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml

## 📖 Description

This is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.  For people that have Nabu-Casa, TTS.cloud-say is far superior to TTS.google_say as it adds languages and gender to the voices available.  If you are a Nabu-Casa subscriber, I highly recommend using this.

This blueprint is set up to watch a binary sensor.  When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice.  The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message.  The delay time and all the other parameters are adjustable.

You will need to select a country code as listed in the TTS.cloud_say documentation listed here:  https://www.nabucasa.com/config/tts/

### ⚙️ Usage

#### 🛠 Installation

* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:

> ◦ https://github.com/SirGoodenough/HA_Blueprints

#### 🧬 To make the blueprint work it will need

> • 1 binary_sensor entities to sense the action you are announcing
>
> • 1 media_player, group of media _players, or list of media_players to send the words to
>
> • Pick a gender and language from https://www.nabucasa.com/config/tts/

Once you have the entities created or decided upon you can build the Automation.  To build the automation:  

> 1. Click on 'Create Automation'  [![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/) and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes
> 4. Set the time-frame that the automation will be active.  Default is always on.
> 5. Select the speaker Gender and Language from the Nabu Casa website
> 6. Enter the messages for when it is found open and when it finally closes
> 7. Set the time delay before the first message and between the open messages

### 🧬 Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. The Trigger section will start everything when your Binary Sensor changes state from off to on.
> 4. Once triggered it goes into a repeat loop that starts with the delay time selected.  This repeat loop will immediately abort if the  binary sensor flips back to off.  If the binary sensor stays on long enough to get passed the delay time, the initial announcement will be sent to the speaker and it will cycle back to the top and start the repeat loop again.
> 5. When the binary_sensor flips to off it will play the closing message,

## 🌞 ❄️ Troubleshooting tip

If you are troubleshooting and you want to see more traces back when doing so, here is a TIP I've found.
Manually edit the automation created with the ui editor (or manually with a text editor) and add the following to have this automation contain 10 traces instead of the normal 5.  Then if the automation is triggering often, you can see the last 10 traces to help you decide what the issue is.

```yaml
alias: aaaaaaa office Fan Test
description: 'See how to increase the number of Traces available''
trace:
  stored_traces: 10
use_blueprint:
.....
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

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan% control & MQTT fan control versions.

https://community.home-assistant.io/t/auto-fan-temp-control-for-3-speed-fan-using-ha-fan-or-mqtt-integration/326419

#### 🧯Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### 🧯Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the multitude of commands from the Xiaomi Magic Cube Remote.

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

#### 🧯Zigbee2MQTT - ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller.

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

#### 🧯ZHA - Xiaomi Cube Controller Blueprint

This Blueprint uses a ZHA built sensor to sort out the 38(+54) commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zha-xiaomi-cube-controller/495975

#### 🧯Device_tracker Monitor & Notifier

This Blueprint Monitor's device_tracker entities that you choose & notifies you if they go offline. Then it gives you the opportunity to devise an action to deal with it.

https://community.home-assistant.io/t/

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough