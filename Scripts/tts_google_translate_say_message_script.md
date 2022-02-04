This Script Blueprint uses Google_translate_say to send the message.  This is the default TTS in Home Assistant.

## :arrow_down: Get Started

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_google_translate_say_message_script.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.yaml

## :page_facing_up: Description

This Script Blueprint uses Google_translate_say to send the message.  This is the default TTS in Home Assistant.

I have my TTS configuration looking like this.  You may need to adjust the blueprint if yours is different:
```
- platform: google_translate
  service_name: google_translate_say
  language: 'en'
```
## :gear: Usage
### Installation
You can import the script blueprint via the button above or manually as below, however it does not show in the UI as there is no Script Blueprint UI and it is not an Automation Blueprint. 
To import this Blueprint: 
>  - Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
>  - Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
>  - In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public REPO on GitHub:
>  ◦   ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_google_translate_say_message_script.yaml```

### Home Assistant
Once installed, go into blueprints and use this to add a script with your variables.  Answer the required questions and you can change or ignore the ones with defaults.  Remember the name you typed in.  For this example, we will suppose you named the script: 
```TTS Test One```
After that, where ever you want this TTS to sound off in another script or an automation, you simply add a service:  (See full examples in my configuration, link below.)

```yaml
- service: script.tts_test_one
```

This makes your automation very clean looking and you move all the 'noisy' code elsewhere.  It has greatly improved my ability to think out automations.  This also keeps me from having to write the same code over and over for every TTS I want to send out.  I have almost 30 different messages in my [Home Assistant Configuration](https://github.com/SirGoodenough/Home-Assistant-Config) 

## :bulb: Fun Ideas
This is a very simple sample test case, I wanted to see if it would work. To my delight I have been replacing all the TTS instances in my configuration with blueprints. It puts all the mess in one place. To call a specific message, I just fire the calling script and I have a 1 liner, done.

I have recently found that the !input will accept templates. Who knew, right? I have a few TTS instances that call for a random response, I just need the sound for timing of something I'm doing, and I found that something like this craziness works. It is the lyrics from a song and when triggered, it just picks one of them to play using random. It also picks a random language to speak the message from the list.  Pretty slick, right?
**NOTE:**  After this was edited to get a pick list, you will need to manually edit the blueprint to change the language to a text input field or you will need to manually edit the script calling blueprint to similar values.

![Sample Script Generation Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/TranslateSayExample.png?raw=true "Example showing Random Selection")

## Changelog

* **2021-08-26**: First blueprint version :tada:
* **2021-11-20**: Changes because of release of Blueprint Script UI
* * Add Minimum Home Assistant 2021-11-0
* **2021-12-15**: Changed link to get language acronyms.  Functionally the same.
* **2021-12-24**: Add pick list of all the available languages,

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