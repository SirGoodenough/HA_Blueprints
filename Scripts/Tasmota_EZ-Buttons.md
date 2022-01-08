## :arrow_down: Get Started

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

I was looking for a Home Assistant Related project and when chatting to Luma from the HASPOne Project a couple of days ago, he mentioned how he uses an MQTT Trick to Generate entities inside of a Blueprint.
This spawned an idea in my head, and Voilia, we have this Blueprint.

I have had these EZY buttons for quite a while on my system.  The idea of the 2 Update Buttons came from Digiblur.  Recently for 2021.12.0 the Home Assistant Team came out with buttons.  I converted my update scripts to buttons.

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
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
>  ◦   https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

#### To make the blueprint work it will need:
> • MQTT Broker happy and running your Tasmota Device connection to Home Assistant
> • Home Assistant 2021.12.0 or newer because that is where the MQTT Button Entity Debuts
> • Home Assistant Tasmota Integration installed and talking to all yout Tasmota Devices.
> • The default GroupTopic of 'Tasmotas' is available on all your Tasmota Devices.
> • This assumes you have left your Tasmota Devices MQTT topic set as the default.  ```%prefix%/%topic%/```  If not you will need to edit this in a couple of places in the Blueprint to match your Tasmota topic.
> • Your Tasmota devices need to be updated to the same 'breaking change' generation as the Released version of Tasmota for this to be able to update.  Currently that is v9.1 minumum.

#### Extended Information
This implementation is exactly the implementation in the Home Assistant Docs.
For further information, reference the links below.
          (https://www.home-assistant.io/integrations/button/)
          (https://www.home-assistant.io/docs/automation/using_blueprints/)
          (https://www.home-assistant.io/integrations/tasmota/)
          (https://tasmota.github.io/docs/Upgrading/)
          (https://tasmota.github.io/docs/Commands/#mqtt)

To build the script:  
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
Example automation:

```yaml
- id: fc3ad7f5-f199-409b-99dc-fb3a0728ecd9
  alias: Power state on HA start-up
  initial_state: on
  trigger:
    - platform: homeassistant
      event: start
  action:
    - delay: 00:00:39
    - alias: Push the Tasmota Reset Button
    - service: button.press
      target:
        entity_id: button.ez_update_button_tasmota
```

## Changelog

* **2022-01-07**: First blueprint version :tada:

## All My Blueprints

* description: A script that uses TTS google_translate_say to send a message to a google speaker  
    https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-and-tts-cloud-say-message-not-an-automation-blueprint/333199 
    source_url: https://gist.github.com/SirGoodenough/ecf747f3bc399f088a13853cf80ec12b 
* description: A script that uses TTS-cloud via Nabu-Casa to send a message to a google speaker 
    https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-and-tts-cloud-say-message-not-an-automation-blueprint/333199 
    source_url: https://gist.github.com/SirGoodenough/7eea35ad75daf883a7938c0bc99499bd
* description: This sets the fan speed for a 3 speed fan (such as an IFAN03/IFAN04) based on a room temperature. 
    https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419 
    source_url: (https://gist.github.com/SirGoodenough/15003002fc5409f029f38914876fa728 
* description: This will accept any 5 button presses or binary sensor detections and use them to preform an action.  RE open a lock, or whatever.
    https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385 
    source_url: https://gist.github.com/SirGoodenough/fbd552e2c93ebaa5c9b3d2b4ebff3297 
* description: This uses tts.cloud_say from Nabu-Casa to tell you a door is open too long and a door has been closed.  
    https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046 
    source_url: https://gist.github.com/SirGoodenough/ed99bd75a65088f4a41c46d1ce19f103 
* description: This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean. 
    https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988 
    source_url: https://gist.github.com/SirGoodenough/0f4ba089a08f78dae6ef2ebb4d058773
* description: This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all. 
    https://community.home-assistant.io/t/ 
    source_url: https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

#### Contact Links or see my other work:
What are we Fixing Today Homepage / Website:        https://www.WhatAreWeFixing.Today/
Channel Link URL: (WhatAreWeFixingToday)             https://bit.ly/WhatAreWeFixingTodaysYT
What are we Fixing Today Facebook page (Sir GoodEnough):         https://bit.ly/WhatAreWeFixingTodaybFB
What are we Fixing Today Twitter Account (Sir GoodEnough):         https://bit.ly/WhatAreWeFixingTodayTW
Discord Guild: (Sir_Goodenough#9683)                     https://discord.gg/Uhmhu3B

#### If you want to support me:
Buy me Coffee:                                        https://www.buymeacoffee.com/SirGoodenough
PayPal one-off donation link:                    https://www.paypal.me/SirGoodenough
Cash App \$CASHTAG:                             https://cash.me/$SirGoodenough
Venmo cash link:                                      https://venmo.com/SirGoodenough 

#WhatAreWeFixingToday
#SirGoodEnough
  