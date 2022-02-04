This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, IE: antenna, FireTV, Chromecast, etc.  The defaults are specific to me and you should change them to match your situation. 

## :arrow_down: Get Started

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FBroadlink_ON_script.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml

## :page_facing_up: Description 

This is a Script Blueprint that takes on the huge mess of scripts created by the Standard Broadlink Integration.  If you have a Broadlink that helps run your TV, you know exactly what I mean.  Every button and function and button sequence on your remote becomes another script that must be called to get stuff done.  It's hard enough to remember what button does what on the remote itself, remembering all the names of the buttons it impoeeible (for me).

The scripts built with this Blueprint gives you a common scenario for turning your stuff on and putting the device in the correct mode to do the things you want to do.  I have a number instances of this blueprint script created in my system.  Here is a shot of them:

![My Buttons in Lovelace](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Screenshot_2022-01-08_20-11-15.png?raw=true "Examples of this Blueprint in Lovelace")

You can import the script blueprint via the button above or manually as below.
To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
>  ◦   ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml```

This is my version and has defaults specific to my system that will need to be changed for your system,  Also if an !input has a default, the calling script is not required to include input data for that !input, but if you want to change the input values without editing the blueprint defaults, then add more selectors to overwrite with your desired values.

## Changelog

* **2021-09-14**: First blueprint version :tada:
* **2021-11-20**: Changes because of release of Blueprint Script UI
* * Add Minimum Home Assistant 2021-11-0

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

Cash App $CASHTAG: https://cash.me/$SirGoodenough

Venmo cash link: https://venmo.com/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough