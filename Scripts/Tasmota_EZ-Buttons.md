This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

NOTE: Version **2022-02-04** to fix a problem that restart of Home Assistant disables the buttons.  Blueprint code has NOT changed.
  See **Other Ideas for your Tasmota EZ Buttons Below**...

## :arrow_down: Get Started

I was looking for a Home Assistant Related project and when chatting to Luma from the HASPOne Project a couple of days ago, he mentioned how he uses an MQTT Trick to Generate entities inside of a Blueprint.
This spawned an idea in my head, and Voilia, we have this Blueprint.

I have had these EZ buttons for quite a while on my system.  The idea of the 2 Update Buttons came from Digiblur.  Recently for 2021.12.0 the Home Assistant Team came out with buttons.  I converted my update scripts to buttons.

After chatting Luma, I put the 2 together, and here we have a Script Blueprint that uses MQTT Discovery to generate 3 buttons for your Tasmota Devices.

#### 1:

    Press a button to restart ALL Tasmota Devices (Also to use during 
    Home Assistant Restart to get all current State and Sensor readings)  

#### 2:

    Press a button to update a couple of Tasmota devices to test that the 
    new version will not break something,  
    (Think of these units as your canary's in the coal mine.)  

#### 3:

    Press a button to update ALL Tasmota devices to the latest version. 

More details and Requirements in the Blueprint Decription and the Input Descriptions.

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FTasmota_EZ-Buttons.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

## :page_facing_up: Description

First, let’s go over Blueprints and what they are.  Blueprints are a way to share scripts (in this case) and is built into Home Assistant.  Simple as that.  You can import my template code and a copy of it will reside in your configuration.  Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build a script.  It will collect the information needed based on your entities and your personal adjustments, and provide a working script.  You will have to have or add the required hardware and entities that the Blueprint needs to function.

### How the Blueprint works:

#### To import this Blueprint: 
* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
* *   https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

#### To make the blueprint work it will need:
* MQTT Broker happy and running your Tasmota Device connection to Home Assistant.
* Home Assistant 2021.12.0 or newer because that is where the MQTT Button Entity Debuts.
* Home Assistant Tasmota Integration installed and talking to all yout Tasmota Devices.
* The default GroupTopic of 'Tasmotas' is available on all your Tasmota Devices.
* This assumes you have left your Tasmota Devices MQTT topic set as the default.  ```%prefix%/%topic%/```  If not you will need to edit this in a couple of places in the Blueprint to match your Tasmota topic.
* Your Tasmota devices need to be updated to the same 'breaking change' generation as the Released version of Tasmota for this to be able to update.  Currently that is v9.1 minumum.

#### Extended Information
This implementation is exactly the implementation in the Home Assistant Docs.
For further information, reference the links below.

>      https://www.home-assistant.io/integrations/button/
>      https://www.home-assistant.io/docs/automation/using_blueprints/
>      https://www.home-assistant.io/integrations/tasmota/
>      https://tasmota.github.io/docs/Upgrading/
>      https://tasmota.github.io/docs/Commands/#mqtt

To build the script:  

[![Open your Home Assistant instance and show your blueprints.](https://my.home-assistant.io/badges/blueprints.svg)](https://my.home-assistant.io/redirect/blueprints/)

> 1. Click on 'Create Script'
> 2. Add a Description so you can tell what this one is for
> 3. Pick the names you want for your buttons or accept the defaults
> 4. The 'ez_canary_grouptopic' selection MUST be in lower_case_chase format for this to function correctly.  Also you need to install this GroupTopic on a select number of your Tasmota Devices.  This allows you to update these first, and you can see if the update is going to work for you before pushing the Update-All Button.  What you put here has to exactly match what you put in your devices.
> 5. The 'ez_canary' name must be changed from the default to enable this button.

#### Generating the Buttons
Once the names have been selected and you click the 'Save Script' button, you only need to execute the script once, and it builds the buttons.
Look in your Devices list for 'Tasmota EZ Buttons'.

[![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

#### Other Ideas

You can effectively use the Tasmota Reset Button to 'reload' all of your Tasmota Devices shortly after you start/restart Home Assistant.  This will give Home assistant a current look at all the states and sensors without relying on retain as it starts up.

UPDATE:  I have noticed that the buttons become disabled after Home Assistant Restart.  Very annoying, but easy to fix.  I have added a start-up Automation to Home Assistant to refresh the buttons a little while after the HA system starts.  The delay is to ensure things are going well and the system is not too busy when this is run.  I have found 22 seconds to be a good number for this on my system, feel free to adjust as needed.  I am also pressing the Tasmota Restart button a little while after that to refresh all the  Tasmota's at boot and provide fresh data for HA to update it's register status. The script name and button name will need to be changed to reflect your choices when you built the blueprint control script.

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

## Changelog

* **2022-01-07**: First blueprint version :tada:
* **2022-02-04**: Add Automation suggestion to fix HA start-up bug.
* **2022-02-07**: Add Retain flag to fix HA start-up bug.

# All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

Here is a list of each of my blueprints, a quick description and jump links to the Blueprints Exchange post...

## Scripts:
#### Broadlink on Script Blueprint

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

#### Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

#### Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean. 

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

#### TTS Cloud Message Blueprint

This Script Blueprint plays a Nabu-Casa tts-cloud-say message in Home Assistant leaving the mess out of the main code.

https://community.home-assistant.io/t/script-blueprint-to-play-nabu-casa-tts-cloud-say-messages-not-an-automation-blueprint/377368

#### TTS Translate Say Message Blueprint

This Script Blueprint plays a Google Translate say message in Home Assistant leaving the mess out of the main code.

https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-not-an-automation-blueprint/333199

## Automations:
#### Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor.  Intended for Ifan03/Ifan04 but useful other places.

https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419

#### Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385


## Contact Links or see my other work:

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## If you want to support me:

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

Cash App \$CASHTAG: https://cash.me/$SirGoodenough

Venmo cash link: https://venmo.com/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough