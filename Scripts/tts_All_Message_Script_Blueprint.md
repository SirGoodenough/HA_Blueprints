📣 This is a script that can use any of 11 integrated TTS Platforms in Home Assistant to send a message to a media player. Some will require Google Type Speakers, some will require Non-Google type speakers. This BP can now be called on-the-fly and change the message & media_player when called.

## 📑 Changelog

* **2023-08-07**: Updates for Home Assistant 2023.8
* * Selector syntax change
* * Condition Selector addition (where applicable)
* * MQTT Discovery name changes (where applicable)
* * Clean-up code formatting
* **2023-07-17**: Updated language lists, external links, formatting, & field default.
* **2023-04-15**: Add ability to feed message and media_player change to script on the fly.
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Changed Choose to if / then statement.
* **2022-04-26**: Add an optional action selector before and after the main TTS for volume, mp3 sounders, sirens, etc.
* **2022-04-11**: Add multiple to Speaker Selection and changed minimum HA to 2022.4.0
* **2022-03-09**: First blueprint version 🎉
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: SCRIPT

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.md#contacts).

Why do I need this?

> This blueprint simplifies the coding required in the Automation/Script calling for a TTS. At that point you only need a service call to run a script to play a pre-planned voice.
>
> The actual mechanics of making the TTS work are in my hands. If HA does an update and breaks it all (again), I will fix the blueprint and you will NOT have to go to 50 places in your yaml code to fix it.

## 🔧 Configuration

Requirements

* Some Version od TTS Installed on your HA instance
* You know how to deal with TTS messaging

## <a name="fields">🗂 Field variables to feed variables from calling automation</a>

    live_message/name: Live Message
        This will change the default message on-the-fly
        required: false

    live_speaker/name: Live Media Player
        Change the default media player on-the-fly
        required: false

## 🗂 Input fields

    b4_action/name: Action before TTS
        This is intended to add a volume
        control action or whatever you want
        to do before sending the TTS message.

    after_action/name: Action after TTS
        This is intended to add a volume
        control action or whatever you want
        to do after sending the TTS message.

    TTS/name: Text to Speech Processor
        Required on ALL *_say platforms.
        Select the configured TTS engine for
        media_player notifications.
        SEE for details: 
        https://www.home-assistant.io/integrations/#text-to-speech

    announcement_message/name: Spoken Message
        Required on ALL *_say platforms.

    speaker_target/name: Entity(s) to speak thru
        Required on ALL *_say platforms.
        Be sure to select the correct type / brand
        of device for the TTS you are using.
        Not All speakers work with all TTS engines.

    speaker_gender/name: Speaker Gender
        Used on most *_say platforms.
        Select speaker gender male or female.
        May not work with all TTS engines.

    baidu_person/name: Baidu Person Code
        Used only on most tts_baidu_say platform.
        This is the voice code of the speaker.

    cloud_language/name: TTS Cloud Language
        This is for Nabu-Casa tts.cloud_say & tts.google_cloud_say.
        See-> https://www.nabucasa.com/config/tts
        NOTE: Not all Language options will have all Genders.

    Google_Cloud_Voice/name: Google Cloud Voice Code
        Used only with tts.google_cloud_say platform. Pick from here-
        https://cloud.google.com/text-to-speech/docs/voices
        This is the voice code of the speaker.
        See-> https://www.home-assistant.io/integrations/google_cloud
        for more information.

    Google_Cloud_Profile/name: Google Cloud Profile
        Used only on most tts.google_cloud_say platform. Pick from here-
        https://cloud.google.com/text-to-speech/docs/audio-profiles
        See-> https://www.home-assistant.io/integrations/google_cloud
        for more information.

    GTS_language/name: TTS Google Translate Say Language
        This is for tts.google_translate_say only. See-> 
        https://cloud.google.com/text-to-speech/docs/voices
        

    marytts_language/name: Language option for tts.marytts_say
        Used only on tts.marytts_say.

    picotts_language/name: Language option for tts.picotts_say
        Used only on tts.picotts_say.

    voicerss_language/name: Language option for tts.voicerss_say
        Used only on tts.voicerss_say.
        See-> https://www.voicerss.org/api for details.

    voicerss_format/name: Message format option for tts.voicerss_say
        Used only on tts.voicerss_say. See->
        https://www.voicerss.org/api for details.

    yandextts_language/name: Language option for tts.yandextts_say
        Used only on tts.yandextts_say. See->
        https://www.home-assistant.io/integrations/yandextts
        for Details.

    yandextts_voice/name: Voice option for tts.yandextts_say
        Used only on tts.yandextts_say. See->
        https://www.home-assistant.io/integrations/yandextts
        for Details.

    yandextts_emotion/name: Emotion option for tts.yandextts_say
        Used only on tts.yandextts_say. See->
        https://www.home-assistant.io/integrations/yandextts
        for Details.

## 👀 ✈️ Extended Information

The main problem I had with building this blueprint is that I do not have all TTS platforms installed in my system, so there is no way I can test everything. I installed what I could and tested those. Others I just have made available the basic configuration of the tts*_say flavor, speaker entity, and message. If the integration page gave me more specific information, I went with that as options.
____________________________
> I am visioning this as a community project. The Github files are available for forking and PR's. Also you can post suggestions in the community tab or on my Discord and we can make changes as changes need to be made. I cannot install and pay for all the versions of TTS out there, and I have not covered any of the custom integrations because I simply do not now what there is a demand for. 
>  
> So if you have ideas and want to help test stuff or want to add some code, let's have fun!
____________________________

All constructive help is encouraged.
____________________________
> **NOTE:** This blueprint replaces 2 other blueprints, so those have been removed from the repository. All the functionality in those has been moved to this one.
>
> * tts_cloud_message_script.yaml
>
> * tts_google_translate_say_message_script.yaml
>


## 🪄 What TTS Integration Can I use?

These integrations are listed here. Please refer to these pages for care and feeding of the *tts_say method you choose.
[⛓ HA TTS Integrations](https://www.home-assistant.io/integrations/#text-to-speech)

This blueprint **WILL NOT** set-up TTS for you. You will be given the opportunity to add the incorrect options that will **NOT** allow your TTS to function. Your best road to success will be to add a TTS session with UI, and only after that is successfully talking to you should you take the languages and options that work there and apply them in this Blueprint. The safest thing to do other than that is to start with the basic sonfiguration for the TTS_say integration that you are using and add options one at a time after you have it working on a base level.

The very basic requirements are for you to provide the *tts_say method that you have installed and tested, the entity that you want to send it to, and the message you want to send. Beyond that likely involves trial and error that may best be done in the Developer Tools Services area here:

**NOTICE:** I have added an action statement both before and after the main TTS call. You can choose to ignore these, or you can use them to change volume, add a media player to play a doorbell, turn on a light, add a delay, whatever you want to do.

[![Open your Home Assistant instance and show your service developer tools.](https://my.home-assistant.io/badges/developer_services.svg)](https://my.home-assistant.io/redirect/developer_services/)

🔥 ***This Blueprint makes the assumption that you already have a tested & proven TTS integration installed and you know how it works and how to use it.*** 🔥

You will need to verify that the name you have given to the TTS integration in your system configuration is the Default name or you need to change this blueprint to use the custom name you have set in the tts: section of configuration.yaml. 🔚

#### 🧬 Home Assistant

Once installed, go into blueprints and use this to add a script with your variables. Answer the required questions and you can change or ignore the ones with defaults. Remember the name you typed in. For this example, we will suppose you named the script:
```TTS Test One```
After that, where ever you want this TTS to sound off in another script or an automation, you simply add a service:  (See full examples in my configuration, link below.)

```yaml
- service: script.tts_test_one
```

This makes your automation very clean looking and you move all the 'noisy' code elsewhere. It has greatly improved my ability to think out automations. This also keeps me from having to write the same code over and over for every TTS I want to send out. I have almost 30 different messages in my [Home Assistant Configuration](https://github.com/SirGoodenough/Home-Assistant-Config)

## <a name="calling">👩‍🍳 Sending TTS messages based on the Calling Automation</a>

As of Version 2021-04-15, thanks to the script Blueprint from [Grumblezz](https://github.com/Grumblezz/Home-Assistant-Notify-Mobile-Companion-App-Devices/blob/main/notify_devices.yaml) I have found a way to feed data into a Script Blueprint. This uses the Key 'fields:'.
Aside from that, what you need to know is you can use this to generate a 'live' TTS response by feeding data into it from an automation that calls this script with data.

To do this, your first step is setting up the Blueprint input fields so that it all works properly with your system. Next you add the input parameters that that you need in order to have the test message coming out of the speaker of your choice. Then save and close the Blueprint Editor. Then you will be able to 'call' this script with a data statement that includes the [field variables in this section](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.md#fields). If you need help formatting the YAML for this you can get some help in the [HA Docs here](https://www.home-assistant.io/integrations/script/#passing-variables-to-scripts). You can also contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.md#contacts).

If you create an automation that calls the script that you created with this BluePrint, you will be able to manually add text or change the speaker. Advanced users will be able to create variables in the automation that can be passed directly to the script to send the TTS message exactly as required.

```yaml
  - service: script.aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaatts_say_testing
    data:
      live_message: |-
        Type something here.
        This is a 2nd line for text. Keep typing for more
```

![Script UI Editor Sample](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/TTS_All_Message_on-the-fly.png?raw=true "Script UI Editor Sample")

## 💡 Fun Ideas

#### Random Response

This is a very simple sample test case, I wanted to see if it would work. To my delight I have been replacing all the TTS instances in my configuration with blueprints. It puts all the mess in one place. To call a specific message, I just fire the calling script and I have a 1 liner, done.

I have recently found that the !input will accept templates. Who knew, right? I have a few TTS instances that call for a random response, I just need the sound for timing of something I'm doing, and I found that something like this craziness works. It is the lyrics from a song and when triggered, it just picks one of them to play using random. It also picks a random language to speak the message from the list. Pretty slick, right?

![Sample Script UI Editor Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/TTS_All_Message_on-the-fly.png?raw=true "Example showing Selections in Script UI Editor")

#### Add MP3 File to TTS Call

Here is an example of playing a sound right before the TTS announcement of a doorbell. Below this picture (unseen) is all the TTS answers specific to your selected TTS and such. This picture is of the top part, the 'Action before TTS' sample, that you can set-up. In this example the sound file is stored on the media folder so it can be picked from the gui.

These action statements can also be used to change volume, flash a light, turn on a siren, anything you like.

![Sample Media_Player Action](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Sample_play_media_action_in_TTS.png?raw=true "Sample Media_Player Action")

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_All_Message_Script_Blueprint.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_All_Message_Script_Blueprint.yaml

# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md```

## <a name="contacts">🤹🏾‍♂️ Contact Links or see my other work</a>

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough