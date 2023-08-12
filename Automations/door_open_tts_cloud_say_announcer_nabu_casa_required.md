This blueprint is set up to watch a binary sensor. When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice. The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message. The delay time and all the other parameters are adjustable.

## 📑 Changelog

* **2023-08-07**: Updates for Home Assistant 2023.8
* * Selector syntax change
* * Condition Selector addition (where applicable)
* * MQTT Discovery name changes (where applicable)
* * Clean-up code formatting
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions.
* **2022-04-11**: Add multiple to Speaker Selection and changed minimum HA to 2022.4.0
* **2022-01-03**: Remove 'Door' restriction on input sensor, and expanded description.
* **2021-12-24**: Add pick list of all the available languages and dialects.
* **2021-10-29**: Add the ability to select the time-frame the announcement will be active
* **2021-09-03**: Add Description
* **2021-06-16**: First blueprint version 🎉 Needs Home Assistant Core 2021.3 or higher and Nabu-Casa to work
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.md#contacts).

Why do I need this?

> This is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange. For people that have Nabu-Casa, TTS.cloud-say is far superior to TTS.google_say as it adds languages and gender to the voices available. If you are a Nabu-Casa subscriber, I highly recommend using this.
>
> This blueprint is set up to watch a binary sensor. When it goes from off to on (closed to open) it triggers a message to be sent to the google enabled speaker of your choice. The message will play after a delay you set and repeat on that same delay until the switch returns to off (closed), at which time it sends a different message. The delay time and all the other parameters are adjustable.
>
> You will need to select a country code as listed in the TTS.cloud_say documentation listed here:  https://www.nabucasa.com/config/tts/
>

## 🔧 Configuration

Requirements

* 1 binary_sensor entities to sense the action you are announcing
* 1 media_player, group of media _players, or list of media_players to send the words to
* Pick a gender and language from https://www.nabucasa.com/config/tts/

## 🗂 Input fields

    people2monitor/name: Person or People to follow
        Select the Person you want this BP to trigger 
        on for this action. Multiples are allowed.

    door_entity/name: 'Door Sensor (or any binary_sensor will do...)'
        Entity that causes the announcement. Actually any entity that 
        changes its state from off to on will work here, You would
        just need to enter the entity manually if it's not a
        binary sensor.

    start_time/name: StartTime
        Time of day you want to enable the announcement each day.

    end_time/name: EndTime
        Time of day you want to disable the announcement each day. 

    speaker_target/Speaker
        Entity to announce event on

    speaker_gender/name: Speaker Gender
        Select speaker gender male or female

    speaker_language/name: Speaker Language
        Select Language code.
        [See here for Details](https://www.nabucasa.com/config/tts/)

    announcement_message/name: Announcement message
        What to say when door is opened

    final_message/name: Final message
        What to say when door is closed.

    cooldown/name: Announcement cooldown
        The minimum number of seconds needed before AND between between
        announcements.

    additional_conditions:
        Extra conditions you may want to add to this automation 
        (Example: Home occupied, TV on, etc)

### 🧬 Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. The Trigger section will start everything when your Binary Sensor changes state from off to on.
> 4. Once triggered it goes into a repeat loop that starts with the delay time selected. This repeat loop will immediately abort if the  binary sensor flips back to off. If the binary sensor stays on long enough to get passed the delay time, the initial announcement will be sent to the speaker and it will cycle back to the top and start the repeat loop again.
> 5. When the binary_sensor flips to off it will play the closing message,

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fdoor_open_tts_cloud_say_announcer_nabu_casa_required.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/door_open_tts_cloud_say_announcer_nabu_casa_required.yaml


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