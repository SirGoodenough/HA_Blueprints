## :arrow_down: Get Started
 This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean. 
 
 I decided I wanted to clean up a bunch of my automations by removing the several lines of YAML every time I wanted to play an mp3 file.  In addition to that, playing specific sound files and other things becomes a simple call to a script file, so really a function.  The actual meat and potatoes of the function is exactly the same for all the sounders and if a change needs to be made, it only has to be made in 1 place in a multiple re-use scenario. 

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgist.github.com%2FSirGoodenough%2F0f4ba089a08f78dae6ef2ebb4d058773)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://gist.github.com/SirGoodenough/0f4ba089a08f78dae6ef2ebb4d058773```

https://gist.github.com/SirGoodenough/0f4ba089a08f78dae6ef2ebb4d058773

## :page_facing_up: Description

First, let’s go over Blueprints and what they are.  Blueprints are a way to share scripts (in this case) and is built into Home Assistant.  Simple as that.  You can import my template code and a copy of it will reside in your configuration.  Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build a script.  It will collect the information needed based on your entities and your personal adjustments, and provide a working script.  You will have to have or add the required hardware and entities that the Blueprint needs to function.

### How the Blueprint works:

#### To import this Blueprint: 
* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
    *   https://gist.github.com/SirGoodenough/0f4ba089a08f78dae6ef2ebb4d058773

#### To make the blueprint work it will need:
> 1 or more functioning media_players
> Media file(s) that are accessible to Home Assistant such that they can be played / displayed thru media_player.

#### Extended Information
This implementation is exactly the implementation in the Home Assistant Docs.
For further information, reference the links below.
>     (https://www.home-assistant.io/more-info/local-media/add-media/)
>     (https://www.home-assistant.io/more-info/local-media/setup-media/)
>     (https://www.home-assistant.io/integrations/media_source/)
>     (https://www.home-assistant.io/integrations/cast/)
>     (https://developers.google.com/cast/docs/media/)

Once you have the entities created or decided upon you can build the Automation.  
To build the script: 

[![Open your Home Assistant instance and show your blueprints.](https://my.home-assistant.io/badges/blueprints.svg)](https://my.home-assistant.io/redirect/blueprints/)

> 1. Click on 'Create Script'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes
> 4. The media_player field will pull from a pick list but you can extend that with multiple media_players or groups as needed by typing them in.  Use the links above to help get your system able to play media files.
> 5. The media type is where you match how the content is encoded with how the player will play it.  Trial and error here can be your friend unless you are much better at figuring this stuff out than me.  I generally only use 'audio/mp3' and occasionally 'image/jpg'.  More detailed information available in the Google Developers link above.

## Changelog

* **2021-12-28**: First blueprint version :tada:

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

    source_url: https://gist.github.com/SirGoodenough/0f4ba089a08f78dae6ef2ebb4d058773
* description: This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all. 
    https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934   

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
 