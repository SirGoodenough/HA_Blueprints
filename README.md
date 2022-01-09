# HA_Blueprints
My Collection of Automation and Script Blueprints for Home Assistant

These are the Blueprints I have created and are sharing with the community.  I have both Script and Automation Blueprints in seperate folders.  Each Blueprint has a file with the .yaml suffix with all the code and a file with the .md suffix which is a markdown description for set-up and usage of the blueprint.  The .md file contains important information and if you want a sucessful install, you should read it.

# All My Blueprints

Here is a list of each of my blueprints, a quick description, and an import link for import to home assistant, and jump links to the Blueprints Exchange post and the files in my GIT Repo...

## Scripts:
#### Broadlink on Script Blueprint

This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, IE: antenna, FireTV, Chromecast, etc.  The defaults are specific to me and you should change them to match your situation. 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FBroadlink_ON_script.yaml)

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

The scripts built with this Blueprint gives you a common scenario for turning your stuff on and putting the device in the correct mode to do the things you want to do.  I have a number instances of this blueprint script created in my system.  Here is a shot of them:

 * [Broadlink_ON_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.md)
 * [Broadlink_ON_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml)


#### Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FTasmota_EZ-Buttons.yaml)

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

* 1) Restart all your Tasmota devices
* 2) Upgrade Selected Tasmota Devices (optional)
* 3) Upgrade all your Tasmota Devices

 * [Tasmota_EZ-Buttons.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.md)
 * [Tasmota_EZ-Buttons.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml)


#### Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean. 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fplay_media_file_script.yaml)

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

 I decided I wanted to clean up a bunch of my automations by removing the several lines of YAML every time I wanted to play an mp3 file.  In addition to that, playing specific sound files and other things becomes a simple call to a script file, so really a function.  The actual meat and potatoes of the function is exactly the same for all the sounders and if a change needs to be made, it only has to be made in 1 place in a multiple re-use scenario. 

 * [play_media_file_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.md)
 * [play_media_file_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.yaml)


#### TTS Cloud Message Blueprint

This Script Blueprint plays a Nabu-Casa tts-cloud-say message in Home Assistant leaving the mess out of the main code.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_cloud_message_script.yaml)

https://community.home-assistant.io/t/script-blueprint-to-play-nabu-casa-tts-cloud-say-messages-not-an-automation-blueprint/377368

This version uses tts_cloud_say to send the message. This is is available only if you are a subscriber to Nabu-Casa.

 * [tts_cloud_message_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.md)
 * [tts_cloud_message_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.yaml)


#### TTS Translate Say Message Blueprint

This Script Blueprint plays a Google Translate say message in Home Assistant leaving the mess out of the main code.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_google_translate_say_message_script.yaml)

https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-not-an-automation-blueprint/333199

This version uses Google Translate Say to send the message. 

 * [tts_google_translate_say_message_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.md)
 * [tts_google_translate_say_message_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.yaml)



## Automations:
#### Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor.  Intended for Ifan03/Ifan04 but useful other places.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FAutoFanControl.yaml)

https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419

This functionality started as a way to help my Bedroom AC unit keep an even temperature throughout the bedroom over night.  My partner wanted the fan on, but not faster than it had to be.  I wanted it to change speeds following the temperature of the room.  So that's what I did.

 * [AutoFanControl.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.md)
 * [AutoFanControl.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.yaml)


#### Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fdoor_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

This blueprint is set up to watch a binary sensor.  When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice.  The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message.  The delay time and all the other parameters are adjustable.

 * [door_open_tts_cloud_say_announcer_nabu_casa_required.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.md)
 * [door_open_tts_cloud_say_announcer_nabu_casa_required.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml)


#### Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fkeypad_5_button_cipher_to_turn_on_something.yaml)

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

Think on this Blueprint as a lock from a common keypad, or a puzzle to solve in a safe house.  
ALSO you can watch the accompanying [YouTube Video](https://youtu.be/ZILTAZQPr_Q) about it here for detailed info!

 * [keypad_5_button_cipher_to_turn_on_something.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.md)
 * [keypad_5_button_cipher_to_turn_on_something.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml)


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