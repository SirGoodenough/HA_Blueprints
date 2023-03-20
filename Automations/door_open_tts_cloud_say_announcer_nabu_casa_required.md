This blueprint is set up to watch a binary sensor. When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice. The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message. The delay time and all the other parameters are adjustable.

## 📑 Changelog

* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions.
* **2022-04-11**: Add multiple to Speaker Selection and changed minimum HA to 2022.4.0
* **2022-01-03**: Remove 'Door' restriction on input sensor, and expanded description.
* **2021-12-24**: Add pick list of all the available languages and dialects.
* **2021-10-29**: Add the ability to select the time-frame the announcement will be active
* **2021-09-03**: Add Description
* **2021-06-16**: First blueprint version 🎉 Needs Home Assistant Core 2021.3 or higher and Nabu-Casa to work
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

Why do I need this?

> This is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange. For people that have Nabu-Casa, TTS.cloud-say is far superior to TTS.google_say as it adds languages and gender to the voices available. If you are a Nabu-Casa subscriber, I highly recommend using this.
>
> This blueprint is set up to watch a binary sensor. When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice. The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message. The delay time and all the other parameters are adjustable.
>
> You will need to select a country code as listed in the TTS.cloud_say documentation listed here:  https://www.nabucasa.com/config/tts/
>

## 🔧 Configuration

Requirements

* 1 binary_sensor entities to sense the action you are announcing
* 1 media_player, group of media _players, or list of media_players to send the words to
* Pick a gender and language from https://www.nabucasa.com/config/tts/

## 🗂 Input fields

    people2monitor/name: Person or People to follow
        Select the Person you want this BP to trigger 
        on for this action. Multiples are allowed.

    door_entity/name: 'Door Sensor (or any binary_sensor will do...)'
        Entity that causes the announcement. Actually any entity that 
        changes its state from off to on will work here, You would
        just need to enter the entity manually if it's not a
        binary sensor.

    start_time/name: StartTime
        Time of day you want to enable the announcement each day.

    end_time/name: EndTime
        Time of day you want to disable the announcement each day. 

    speaker_target/Speaker
        Entity to announce event on

    speaker_gender/name: Speaker Gender
        Select speaker gender male or female

    speaker_language/name: Speaker Language
        Select Language code.
        [See here for Details](https://www.nabucasa.com/config/tts/)

    announcement_message/name: Announcement message
        What to say when door is opened

    final_message/name: Final message
        What to say when door is closed.

    cooldown/name: Announcement cooldown
        The minimum number of seconds needed before AND between between
        announcements.

### 🧬 Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. The Trigger section will start everything when your Binary Sensor changes state from off to on.
> 4. Once triggered it goes into a repeat loop that starts with the delay time selected. This repeat loop will immediately abort if the  binary sensor flips back to off. If the binary sensor stays on long enough to get passed the delay time, the initial announcement will be sent to the speaker and it will cycle back to the top and start the repeat loop again.
> 5. When the binary_sensor flips to off it will play the closing message,

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fdoor_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml


# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

Here is a list of each of my blueprints, a quick description and jump links to the Blueprints Exchange post...

## 🌀 Scripts

#### 🧯Broadlink on Script Blueprint

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, Pushes remote buttons in sequence.

#### 🧯Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base. Restart All, Update a few, and Update all.

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

This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water. This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

https://community.home-assistant.io/t/humidifier-water-throttle-control/527583

#### 🧯 Person_Alert_Blueprint

This BluePrint will monitor a person or persons, and when they 'enter' or 'leave' the zone or zones you pick, it will trigger an action for both enter and leave phases. Yes, it will watch multiple people and multiple zones at the same time!

https://community.home-assistant.io/t/person-alert-blueprint/542209

#### 🧯 Octoprint_Additional_Buttons_Helper

This is Blueprint is provided as a helper for people using the Octoprint Plugin called OctoPrint-HomeAssistant. What this does is add 6 buttons, 4 of which you as the user can set your own G-Codes to for customizing. Also adds safe shutdown and presentation functions.

https://community.home-assistant.io/t/octoprint-additional-buttons-helper-blueprint/549826

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough