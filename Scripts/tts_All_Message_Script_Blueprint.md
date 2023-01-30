📣 This is a script that can use any of the 11 integrated TTS Platforms in Home Assistant to send a message to a media player. Some will require Google Type Speakers, some will require Non-Google type speakers.

## 📑 Changelog

* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Changed Choose to if / then statement.
* **2022-04-26**: Add an optional action selector before and after the main TTS for volume, mp3 sounders, sirens, etc.
* **2022-04-11**: Add multiple to Speaker Selection and changed minimum HA to 2022.4.0
* **2022-03-09**: First blueprint version 🎉

## 📩 * Version Updates

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

🔗 There is not an official version control system for Blueprints.  However I have found something that comes pretty close.  It is not perfect, but for **MOST** Blueprints, it does just fine.  I encourage you to check this script out and use it to easily check if I have updated this blueprint.

[koter84 Blueprint Update Script](https://gist.github.com/koter84/86790850aa63354bda56d041de31dc70#file-readme-md)

## 📩 Get Started

he main problem I had with this blueprint is that I do not have all TTS platforms installed in my system, so there is no way I can test everything.  I installed what I could and tested those. Others I just have made available the basic configuration of the tts*_say flavor, speaker entity, and message. If the integration page gave me more specific information, I went with that as options.

____________________________
> I am visioning this as a community project. The Github files are available for forking and PR's. Also you can post suggestions in the community tab or on my Discord and we can make changes as changes need to be made.  I cannot install and pay for all the versions of TTS out there, and I have not covered any of the custom integrations because I simply do not now what there is a demand for.  
So if you have ideas and want to help test stuff or want to add some code, let's have fun!
____________________________

All constructive help is encouraged.
____________________________
> **NOTE:** This blueprint replaces 2 other blueprints, so those have been removed from the repository.  All the functionality in those has been moved to this one.
>
> * tts_cloud_message_script.yaml
>
> * tts_google_translate_say_message_script.yaml
>
___________________________

### Option 1: My Home Assistant

Click the badge to import this Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_All_Message_Script_Blueprint.yaml)

# Please Click the 🧡 at the end of the Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.yaml

## 📖 Description

These integrations are listed here. Please refer to these pages for care and feeding of the *tts_say method you choose.
⛓ https://www.home-assistant.io/integrations/#text-to-speech

This blueprint **WILL NOT** set-up TTS for you. You will be given the opportunity to add the incorrect options that will **NOT** allow your TTS to function. Your best road to success will be to add a TTS session with UI, and only after that is successfully talking to you should you take the languages and options that work there and apply them in this Blueprint. The safest thing to do other than that is to start with the basic sonfiguration for the TTS_say integration that you are using and add options one at a time after you have it working on a base level.

The very basic requirements are for you to provide the *tts_say method that you have installed and tested, the entity that you want to send it to, and the message you want to send. Beyond that likely involves trial and error that may best be done in the Developer Tools Services area here:

**NOTICE:** I have added an action statement both before and after the main TTS call.  You can choose to ignore these, or you can use them to change volume, add a media player to play a doorbell, turn on a light, add a delay, whatever you want to do.

[![Open your Home Assistant instance and show your service developer tools.](https://my.home-assistant.io/badges/developer_services.svg)](https://my.home-assistant.io/redirect/developer_services/)

🔥 ***This Blueprint makes the assumption that you already have a tested & proven TTS integration installed and you know how it works and how to use it.*** 🔥

You will need to verify that the name you have given to the TTS integration in your system configuration is the Default name or you need to change this blueprint to use the custom name you have set in the tts: section of configuration.yaml. 🔚

### ⚙️ Usage

#### 🛠 Installation

* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:

> ◦ https://github.com/SirGoodenough/HA_Blueprints

#### 🧬 Home Assistant

Once installed, go into blueprints and use this to add a script with your variables.  Answer the required questions and you can change or ignore the ones with defaults.  Remember the name you typed in.  For this example, we will suppose you named the script:
```TTS Test One```
After that, where ever you want this TTS to sound off in another script or an automation, you simply add a service:  (See full examples in my configuration, link below.)

```yaml
- service: script.tts_test_one
```

This makes your automation very clean looking and you move all the 'noisy' code elsewhere.  It has greatly improved my ability to think out automations.  This also keeps me from having to write the same code over and over for every TTS I want to send out.  I have almost 30 different messages in my [Home Assistant Configuration](https://github.com/SirGoodenough/Home-Assistant-Config)

## 💡 Fun Ideas

#### Random Response

This is a very simple sample test case, I wanted to see if it would work. To my delight I have been replacing all the TTS instances in my configuration with blueprints. It puts all the mess in one place. To call a specific message, I just fire the calling script and I have a 1 liner, done.

I have recently found that the !input will accept templates. Who knew, right? I have a few TTS instances that call for a random response, I just need the sound for timing of something I'm doing, and I found that something like this craziness works. It is the lyrics from a song and when triggered, it just picks one of them to play using random. It also picks a random language to speak the message from the list.  Pretty slick, right?

![Sample Script Generation Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/TranslateSayExample.png?raw=true "Example showing Random Selection")

#### Add MP3 File to TTS Call

Here is an example of playing a sound right before the TTS announcement of a doorbell.  Below this picture (unseen) is all the TTS answers specific to your selected TTS and such.  This picture is of the top part, the 'Action before TTS' sample, that you can set-up. In this example the sound file is stored on the media folder so it can be picked from the gui.

These action statements can also be used to change volume, flash a light, turn on a siren, anything you like.

![Sample Media_Player Action](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Sample_play_media_action_in_TTS.png?raw=true "Sample Media_Player Action")

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

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan % control & MQTT fan control versions.

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

#### 🧯 Zigbee2MQTT Aqara Magic Cube T1-Pro CTP-R01 Xiaomi Lumi cagl02

This Blueprint gives you literally hundreds of actions available on the new Magic Cube.

https://community.home-assistant.io/t/zigbee2mqtt-aqara-magic-cube-t1-pro-ctp-r01-xiaomi-lumi-cagl02/525111

#### 🧯 Humidifier Water Throttle Control

This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water.  This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

https://community.home-assistant.io/t/humidifier-water-throttle-control/527583

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough