This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.  Thisk a lock from a common keypad, or a puzzle to solve in a safe house.  
ALSO you can watch the accompanying [YouTube Video](https://youtu.be/ZILTAZQPr_Q) about it here for detailed info!

## 📑 Changelog

* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions plus shortcut and.
* **2021-11-20**: Add Minimum Home Assistant version.
* **2021-09-03**: Add Description.
* **2021-08-04**: Add comments and cleanup.
* **2021-07-21**: Add the watchdog timeout test.
* **2021-07-11**: First blueprint version :tada: Needs Home Assistant Core 2021.7 or higher for Trigger_ID to work

## 📩  Get Started

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint (needs Home Assistant Core 2021.7 or higher for Trigger_ID to work)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fkeypad_5_button_cipher_to_turn_on_something.yaml)

# Please Click the 🧡 at the end of the Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml

## 📖 Description

This all started out with my <a href="https://whatarewefixing.today/125/tasmota-based-drop-pin-door-lock/" target="_blank">Less Than $30 Drop Pin Lock</a> Project that I installed a couple of years ago in my house.  These locks had the unfortunate problem of not having a way to unlock them from the outside without Google Home or the Home Assistant App on your phone.  I always wanted to create a keypad that would function in this manner, and until the addition of the Trigger_ID feature in Home Assistant 2021.7, the Automation while possible, would involve extensive use of complicated templating that I was not in the mood to build.  Trigger_ID’s made it simple!

First, let’s go over Blueprints and what they are.  Blueprints are a way to share automations and is built into Home Assistant.  Simple as that.  You can import my template code and a copy of it will reside in your configuration.  Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build an automation.  It will collect the information needed based on your entities and your personal adjustments, and provide a working automation.  You will have to have or add the required hardware and entities that the Blueprint needs to function.

### ⚙️ How the Blueprint works:

To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
>
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
>
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:
> ◦ https://github.com/SirGoodenough/HA_Blueprints

To make the blueprint work it will need:
> • 5 binary_sensor entities to sense the button presses
>
> • 1 input_boolean entity as the feature to trigger the lock action  [![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)
>
> • 1 input_number entity to store the internal sequence number

The binary sensors can be the inputs from a device like I have OR it can be existing devices.  For instance if you want to walk into your back porch and use the PIR as button one, then in sequence you trigger the freezer door, the light switch on the wall, the doorbell, and the fridge door, then that can be your door unlock sequence.  No keypad needed!  I personally bought an RM433 from Itead / Sonoff and plugged the number codes into my RF-Bridge set-up and went with that.

Once you have the entities created or decided upon you can build the Automation.  To build the automation:

> 1. Click on 'Create Automation'  [![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/) and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes
> 4. Select a Lock On time in seconds.  This is how long the input_boolean stays on before the lock is released.
> 5. Test that your Cipher works by pressing the buttons and watching the result.

To get your lock to open, build a simple automation using the UI (or manually) that triggers on your input boolean, and the action is opening your lock or whatever you want to do.  For example:

```yaml
  - id: 0b408ade-16fd-42fc-8333-518660b421ae
    mode: single
    max_exceeded: silent
    alias: test lock
    initial_state: on
    trigger:
      - platform: state
        entity_id: input_boolean.pad_enable
    action:
      - service: lock.unlock
        data:
          code: '7554288'
        target:
          entity_id: lock.side_door
```

### ⚙️ Usage

#### 🛠 Installation

* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:

> ◦ https://github.com/SirGoodenough/HA_Blueprints

#### 🧬 Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. In the Variables section has several entries. The first is needed to convert the !input: variable of the input_number into a variable so that it can be used in a template. After that we grab and store the last time the sequence number was changed, the actual value of the sequence number, and the current time. These are used for the watchdog so that the code cannot be accidentally left ‘almost’ triggered.
> 4. In the trigger section there is a trigger for each button, watching for that button to be pressed. When the button is pressed, a trigger_id is generated and passed along to the action: section so it knows which trigger was initiated.
> 5. In the action: section the always executed first part is the watchdog. It checks that the last time the sequence number was changed was within the last 5 minutes. Otherwise if the sequence was left at the 4th button for a week, all someone would have to do it hit the 5th button and it would open the lock.
The rest is one big choose: statement. To get button 1 to be accepted you only need the button 1 trigger_ID and this changes the sequence code number. In order to get to stage 2 of the cipher, both the trigger_ID and the sequence number have to be correct, and once it is, it again changes the sequence number. This pattern is repeated until the fifth number is pressed with the correct sequence code set and that fires the input_boolean to open the lock. Should you press the numbers in the wrong order, the cipher resets and you need to know to start over. Pressing button 1 again will also reset the sequence via the default action in the choose code.

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

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough
