This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base. Restart All, Update a few, and Update all.

## 📑 Changelog

* **2023-08-07**: Updates for Home Assistant 2023.8
  * (Documentation change 2-7-2024 to add License notice. Changes only to Descriptions.)
  * LOOK [THIS LINK](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Update_Instructions/Update--Tasmota_EZ-Buttons.md) FOR IMPORTANT UPDATE INSTRUCTIONS
  * Selector syntax change
  * Condition Selector addition (where applicable)
  * MQTT Discovery name changes (where applicable)
  * Clean-up code formatting
* **2023-05-01**: Bug Fix missing commas
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
  * Name of Blueprint may have changed meaing you have to re-download with a new link.
  * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added shortcut and.
  * Add alternate MQTT topic format
* **2022-02-07**: Add Retain flag to fix HA start-up bug.
* **2022-02-04**: Add Automation suggestion to fix HA start-up bug.
* **2022-01-07**: First blueprint version 🎉

<base target="_blank"\>

## 🔮 About this blueprint

Type of blueprint: SCRIPT

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.md#contacts).

Why do I need this?

> If you are not very good with Home Assistant script writing, but want help managing your Tasmota firmware devices, this is the Blueprint for you.
>
> This BP generates 3 buttons (scripts). It does this using MQTT Discovery. My assumption is that your Home Assistant Instance has access to an MQTT Broker because you are using Tasmota, which all but requires it. If you are not connected to an MQTT Broker, this BP will not work for you. 
> 
> Button one will simply restart all your Tasmota devices. This comes in handy at HA re-boot to refresh the state of the devices in Home Assistant. This means all the temperature, etc. measurements are up to date and displayed on the dashboard right away, not after the refresh delay. Also good for troubleshooting problem devices, giving them a kick when they need it.
>
> The second Button will update a few of your Tasmota Devices to the latest firmware. That is assuming you start out kind of caught up already and have followed the [upgrade path](https://tasmota.github.io/docs/Upgrading/)
> The reason for upgrading a few is to verify that the upgrade is working with your things and prove to yourself that it is safe to upgrade them all. I have almost 40 devices, so I grab like 1 of each type and add them here. Then when a new Tasmota version shows up, I click this and those 5 (in my case) devices upgrade. After that is working for a few days without problems, I click the next button.
>
> The third Button just upgrades everything to the latest version. I can upgrade all my devices in about 3 minutes like this. [My Youtube Short](https://www.youtube.com/watch?v=OT5id_P2JVw)

#### 🗿License Notice:

* Copies of the original Blueprint that were converted via the 'Take Control' feature or other means are officially not supported by me.

* I may or may not be able to support you when you have a problem after you make changes to my code, as some of the code is no longer mine.

* I & my license also require attribution as a link back to the original should you use this code in your own creation.

* [Here is a link to my license & the original github post](https://github.com/SirGoodenough/HA_Blueprints?tab=License-1-ov-file) expected to be followed & referenced as attribution should you use this code elsewhere.

## 🔧 Configuration

Requirements

* MQTT Broker happy and running your Tasmota Device connection to Home Assistant.
* Home Assistant 2021.12.0 or newer because that is where the MQTT Button Entity Debuts.
* Home Assistant Tasmota Integration installed and talking to all yout Tasmota Devices.
* The default GroupTopic of 'Tasmotas' is available on all your Tasmota Devices.
* Tasmota Devices firmware default MQTT topic is set to: ```%prefix%/%topic%/``` If you did not change the topic in your Tasmota Devices then leave it as the default here as well. The other option available to you is to flip them as I do in my Home Assistant personally.
* Your Tasmota devices need to be updated to the same 'breaking change' generation as the Released version of Tasmota for this to be able to update. Currently that is v9.1 minimum.

## 🗂 Input fields

    ez_update:/name: EZ Update Button Tasmota
        This is the name of the button you want to use for updating ALL your
        Tasmota instances. It will use the built-in groupTopics in Tasmota
        to send the update command to all devices. 

    topic_format:/name: Tasmota Topic Format
        The format of your Tasmota devices has a default that most people use:  
        '%prefix%/%topic%/'. 

    ez_canary:/name: EZ Canary Button Tasmota
        This is the name of the button you want to use for the test new version
        select sample. I suggest use 5 or less Tasmota devices for this list. 
        Leave this as 'not_selected' if you do not plan on using this feature. 
        Leaving this Blank will cause errors.
        Will be converted to lower-case-chase
        
    ez_canary_grouptopic:/name: The GroupTopic name for the EZ Canary Button
        This is the name you assigned to the GroupTopics in the devices 
        you chose as the first ones to receive a firmware update. 
        This needs to be set-up by you in the Tasmota Console of the devices 
        themselves. Leave this blank if you are not using this feature.
        The button will be created, but it won't do anything.

    ez_restart:/name: EZ Restart Button Tasmota
        This is the name of the button you want to use for restarting all
        Tasmota devices.

## 👀 ✈️ Extended Information

For further information, reference these links below.

>      https://www.home-assistant.io/integrations/button/
>      https://www.home-assistant.io/docs/automation/using_blueprints/
>      [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)
>      https://www.home-assistant.io/integrations/tasmota/
>      https://tasmota.github.io/docs/Upgrading/
>      https://tasmota.github.io/docs/Commands/#mqtt

## 🗣 Generating the Buttons

Once the names have been selected and you click the 'Save Script' button, you only need to execute the script once, and it builds the buttons.
Look in your Devices list for 'Tasmota EZ Buttons'.

[![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

## 💡 Other Ideas

You can effectively use the Tasmota Reset Button to 'reload' all of your Tasmota Devices shortly after you start/restart Home Assistant. This will give Home assistant a current look at all the states and sensors without relying on retain as it starts up.

UPDATE:  I have noticed that the buttons become disabled after Home Assistant Restart. Very annoying, but easy to fix. I have added a start-up Automation to Home Assistant to refresh the buttons a little while after the HA system starts. The delay is to ensure things are going well and the system is not too busy when this is run. I have found 22 seconds to be a good number for this on my system, feel free to adjust as needed. I am also pressing the Tasmota Restart button a little while after that to refresh all the Tasmota's at boot and provide fresh data for HA to update it's register status. The script name and button name will need to be changed to reflect your choices when you built the blueprint control script.

Example [automation code sample file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Tasmota_EZ-Buttons_Home_Assistant_Start-up_Automation_SAMPLE.yaml).

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FTasmota_EZ-Buttons.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.yaml

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