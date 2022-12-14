This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base. Restart All, Update a few, and Update all.

## 📑 Changelog

* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added shortcut and.
* * Add alternate MQTT topic format
* **2022-02-07**: Add Retain flag to fix HA start-up bug.
* **2022-02-04**: Add Automation suggestion to fix HA start-up bug.
* **2022-01-07**: First blueprint version :tada:

## 📩 * Version Updates

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

🔗 There is not an official version control system for Blueprints.  However I have found something that comes pretty close.  It is not perfect, but for **MOST** Blueprints, it does just fine.  I encourage you to check this script out and use it to easily check if I have updated this blueprint.

[koter84 Blueprint Update Script](https://gist.github.com/koter84/86790850aa63354bda56d041de31dc70#file-readme-md)

## 📩 Get Started

I was looking for a Home Assistant Related project and when chatting to Luma from the HASPOne Project a couple of days ago, he mentioned how he uses an MQTT Trick to Generate entities inside of a Blueprint.
This spawned an idea in my head, and Voilia, we have this Blueprint.

I have had these EZ buttons for quite a while on my system.  The idea of the 2 Update Buttons came from Digiblur. Recently for 2021.12.0 the Home Assistant Team came out with buttons. I converted my update scripts to buttons.

After chatting Luma, I put the 2 together, and here we have a Script Blueprint that uses MQTT Discovery to generate 3 buttons for your Tasmota Devices.

#### 1>

    Press a button to restart ALL Tasmota Devices (Also to use during 
    Home Assistant Restart to get all current State and Sensor readings)  

#### 2>

    Press a button to update a couple of Tasmota devices to test that the 
    new version will not break something,  
    (Think of these units as your canary's in the coal mine.)  

#### 3>

    Press a button to update ALL Tasmota devices to the latest version. 

More details and Requirements in the Blueprint Decription and the Input Descriptions.

### Option 1: My Home Assistant

Click the badge to import this Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FTasmota_EZ-Buttons.yaml)

# Please Click the 🧡 at the end of the Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

## 📖 Description

First, let’s go over Blueprints and what they are. Blueprints are a way to share scripts (in this case) and is built into Home Assistant. Simple as that. You can import my template code and a copy of it will reside in your configuration. Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build a script. It will collect the information needed based on your entities and your personal adjustments, and provide a working script. You will have to have or add the required hardware and entities that the Blueprint needs to function.

### ⚙️ Usage

#### 🛠 Installation

* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’. A selection box should pop up. Type blue and select the button to navigate to blueprints. You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:

> ◦ https://github.com/SirGoodenough/HA_Blueprints

#### 🧬 To make the blueprint work it will need

* MQTT Broker happy and running your Tasmota Device connection to Home Assistant.
* Home Assistant 2021.12.0 or newer because that is where the MQTT Button Entity Debuts.
* Home Assistant Tasmota Integration installed and talking to all yout Tasmota Devices.
* The default GroupTopic of 'Tasmotas' is available on all your Tasmota Devices.
* Tasmota Devices firmware default MQTT topic is set to: ```%prefix%/%topic%/``` If you did not change the topic in your Tasmota Devices then leave it as the default here as well. The other option available to you is to flip them as I do in my Home Assistant personally.
* Your Tasmota devices need to be updated to the same 'breaking change' generation as the Released version of Tasmota for this to be able to update. Currently that is v9.1 minumum.

#### ✈️ Extended Information

This implementation is exactly the implementation in the Home Assistant Docs.
For further information, reference the links below.

>      https://www.home-assistant.io/integrations/button/
>      https://www.home-assistant.io/docs/automation/using_blueprints/
>      https://www.home-assistant.io/integrations/tasmota/
>      https://tasmota.github.io/docs/Upgrading/
>      https://tasmota.github.io/docs/Commands/#mqtt

To build the script:  

[![Open your Home Assistant instance and show your blueprints.](https://my.home-assistant.io/badges/blueprints.svg)](https://my.home-assistant.io/redirect/blueprints/)

> 1. Click on 'Create Script' [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)  and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Pick the names you want for your buttons or accept the defaults
> 4. The 'ez_canary_grouptopic' selection MUST be in lower_case_chase format for this to function correctly. Also you need to install this GroupTopic on a select number of your Tasmota Devices. This allows you to update these first, and you can see if the update is going to work for you before pushing the Update-All Button. What you put here has to exactly match what you put in your devices.
> 5. The 'ez_canary' name must be changed from the default to enable this button.

#### 🗣 Generating the Buttons

Once the names have been selected and you click the 'Save Script' button, you only need to execute the script once, and it builds the buttons.
Look in your Devices list for 'Tasmota EZ Buttons'.

[![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

#### 💡 Other Ideas

You can effectively use the Tasmota Reset Button to 'reload' all of your Tasmota Devices shortly after you start/restart Home Assistant. This will give Home assistant a current look at all the states and sensors without relying on retain as it starts up.

UPDATE:  I have noticed that the buttons become disabled after Home Assistant Restart. Very annoying, but easy to fix. I have added a start-up Automation to Home Assistant to refresh the buttons a little while after the HA system starts. The delay is to ensure things are going well and the system is not too busy when this is run. I have found 22 seconds to be a good number for this on my system, feel free to adjust as needed. I am also pressing the Tasmota Restart button a little while after that to refresh all the Tasmota's at boot and provide fresh data for HA to update it's register status. The script name and button name will need to be changed to reflect your choices when you built the blueprint control script.

Example automation:

```yaml
####################################################
# MQTT Restart Tasmota                             #
####################################################
####    Use this automation to get all your devices in sync, including
####     power state, immediately after Home Assistant is (re)started.
- id: Tasmota_Restart_Sequence-random-oisjg98uwr8ytjw9ut8344
  alias: Power state on HA start-up
  initial_state: on
  trigger:
    - platform: homeassistant
      event: start
  action:
    - delay: 00:00:22
    - alias: Make sure EZ Buttons are active
      service: script.tasmota_ez_button_for_update_and_restart_all_2022_01_07a
    - delay: 00:00:22
    - alias: Push the Tasmota Restart - One Button to Rule them All
      service: button.press
      target:
        entity_id: button.ez_restart_button_tasmota
```

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

TThis Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan % control & MQTT fan control versions.

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

https://community.home-assistant.io/t/device-tracker-monitor-notifier/500688

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough