# HA_Blueprints
My Collection of Automation and Script Blueprints for Home Assistant

These are the Blueprints I have created and are sharing with the community.  I have both Script and Automation Blueprints in seperate folders.  Each Blueprint has a file with the .yaml suffix with all the code and a file with the .md suffix which is a markdown description for set-up and usage of the blueprint.  The .md file contains important information and if you want a sucessful install, you should read it.

Here is a list of each blueprint, the description file for it, a quick description, and an import link for import to home assistant...

## Scripts:
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

https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-and-tts-cloud-say-message-not-an-automation-blueprint/333199

This version uses tts_cloud_say to send the message. This is is available only if you are a subscriber to Nabu-Casa.

 * [tts_cloud_message_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.md)
 * [tts_cloud_message_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.yaml)


#### TTS Cloud Message Blueprint

This Script Blueprint plays a Google Translate say message in Home Assistant leaving the mess out of the main code.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_google_translate_say_message_script.yaml)

https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-and-tts-cloud-say-message-not-an-automation-blueprint/333199


 * [tts_google_translate_say_message_script.md Help File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.md)
 * [tts_google_translate_say_message_script.yaml Code File](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.yaml)



## Automations:

* description: This sets the fan speed for a 3 speed fan (such as an IFAN03/IFAN04) based on a room temperature. 
    https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419 

    source_url: (https://gist.github.com/SirGoodenough/15003002fc5409f029f38914876fa728 
* description: This will accept any 5 button presses or binary sensor detections and use them to preform an action.  RE open a lock, or whatever.
    https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385 

    source_url: https://gist.github.com/SirGoodenough/fbd552e2c93ebaa5c9b3d2b4ebff3297 
* description: This uses tts.cloud_say from Nabu-Casa to tell you a door is open too long and a door has been closed.  
    https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046 

    source_url: https://gist.github.com/SirGoodenough/ed99bd75a65088f4a41c46d1ce19f103 
    

### Contact Links or see my other work:

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

### If you want to support me:

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

Cash App $CASHTAG: https://cash.me/$SirGoodenough

Venmo cash link: https://venmo.com/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough