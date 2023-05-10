This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean.

## 📑 Changelog

* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-04-11**: Add multiple to Speaker Selection and changed minimum HA to 2022.4.0
* **2021-12-28**: First blueprint version 🎉
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: SCRIPT

Why do I need this?

> I decided I wanted to clean up a bunch of my automations by removing the several lines of YAML every time I wanted to play an mp3 file. 
> 
> In addition to that, playing specific sound files and other things becomes a simple call to a script file, so really a function. The actual meat and potatoes of the function is exactly the same for all the sounders and if a change needs to be made, it only has to be made in 1 place in a multiple re-use scenario.
>

## 🔧 Configuration

Requirements

* 1 or more functioning media_players
* Media file(s) that are accessible to Home Assistant such that they can be played / displayed thru media_player.
* The speakers you want to broadcast to must be working and integrated with the integration that makes them work. This BP does not set-up speakers for you, it only sends files to the speakers. See [Links](#%EF%B8%8F-extended-information) below to help guide you thru speaker set-up.

## 🗂 Input fields

    speaker_target:/ name: Device(s) to send the file to
        Add the media_player that you want to play this on. 
          Multiples are allowed.

    file_2_play:/ name: Media File to play
        The media file name needs to be put here. 
        Please include the path that is accessible to the media player. 
        A sample path may be 'media-source://media_source/local/sample_file.mp3'.
        See more information here: 
          (https://www.home-assistant.io/more-info/local-media/add-media/)
          (https://www.home-assistant.io/more-info/local-media/setup-media/)
          (https://www.home-assistant.io/integrations/media_source/)

    media_type:/ name: Media_Content_type
        This is where you match how the content is encoded with 
        how the player will play it. Trial and error here can be your friend 
        unless you are much better at figuring this stuff out than me. 
        I generally only use 'audio/mp3' and occasionally 'image/jpg'. 
        More detailed information available here: 
          (https://www.home-assistant.io/integrations/cast/)
          (https://developers.google.com/cast/docs/media/)

## ✈️ Extended Information

For further information, reference these links below.

>     (https://www.home-assistant.io/more-info/local-media/add-media/)
>     (https://www.home-assistant.io/more-info/local-media/setup-media/)
>     (https://www.home-assistant.io/integrations/media_source/)
>     (https://www.home-assistant.io/integrations/cast/)
>     [![Open your Home Assistant instance and browse available media.](https://my.home-assistant.io/badges/media_browser.svg)](https://my.home-assistant.io/redirect/media_browser/)
>     (https://developers.google.com/cast/docs/media/)

## 👀 Installation example

Once you have the entities created or decided upon you can build the Script. 

To build the script:

[![Open your Home Assistant instance and show your blueprints.](https://my.home-assistant.io/badges/blueprints.svg)](https://my.home-assistant.io/redirect/blueprints/)

> 1. Click on 'Create Script' [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)  and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes
> 4. The media_player field will pull from a pick list but you can extend that with multiple media_players or groups as needed by typing them in. Use the links above to help get your system able to play media files.
> 5. The media type is where you match how the content is encoded with how the player will play it. Trial and error here can be your friend unless you are much better at figuring this stuff out than me. I generally only use 'audio/mp3' and occasionally 'image/jpg'. More detailed information available in the Google Developers link above.

## 🥧 Example Usage

This is a case I use this in my setup. Instead of pasting all the media set-up code in an already busy automation, I set that stuff up with this blueprint and just call the script when I want to to play. The added bonus is I can call on this script again where appropriate and the sounder is just a script call away.

See YAML code in this [Sample YAML file / package file](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/play_media_file_script_SAMPLE.yaml)

## 🌞 ❄️ Troubleshooting tip

If you are troubleshooting and you want to see more traces back when doing so, here is a TIP I've found.
Manually edit the automation created with the ui editor (or manually with a text editor) and add the following to have this automation contain 10 traces instead of the normal 5. Then if the automation is triggering often, you can see the last 10 traces to help you decide what the issue is.
[HA Docs on this here.](https://www.home-assistant.io/docs/automation/troubleshooting/#traces)

```yaml
trace:
  stored_traces: 10
```

## 📩 **Version Updates**

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

📩 There is not an official version control system for Blueprints. However I have found something that comes pretty close. It is not perfect, but for **MOST** Blueprints, it does just fine. I encourage you to check this script out and use it to easily check if I have updated this blueprint. [🔗koter84 Blueprint Update Script ](https://github.com/koter84/HomeAssistant_Blueprints_Update/)

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fplay_media_file_script.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/play_media_file_script.yaml

# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md```

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough