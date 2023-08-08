This Blueprint is for controlling a 3 speed fan based on a temp sensor reading. There is a version for a 3 speed MQTT Fan & another version that communicates thru a Home Assistant fan entity using speed percentages.

## 📑 Changelog

* **2023-08-07**: Updates for Home Assistant 2023.8
* * Selector syntax change
* * Condition Selector addition (where applicable)
* * MQTT Discovery name changes (where applicable)
* * Clean-up code formatting
* **2023-07-19**: Remove Helper on MQTT version
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-26**: BugFix. Time default no longer all zeros. Update default Tnx: [cappadanna](https://community.home-assistant.io/u/cappadanna)
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaning you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-15-A**: Minor code clean-up on Casting, no functional change.
* * Updated AirCon Start Example code to include start AirCon only if warm enough in room.
* **2022-05-15**: Add 2nd Blueprint triggered with HA fan entity, otherwise identical.
* **2022-05-12.1**: Change MQTT QOS to 2
* **2022-05-12**: Added support for weekday control
* * Added Action Selectors to the 'fan' & 'all done' loops for controlling AirCon or Heat or anything.
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions plus shortcut and & or.
* **2022-02-07**: Add Default value to float filters (for HA Breaking change).
* **2021-11-20**: Add Minimum Home Assistant version.
* **2021-09-03**: Add Description.
* **2021-08-19**: Remove negative Temp Gap hysteresis, logic wrong.
* **2021-08-04**: Remove Default path as it made my fan beep for no reason.
* **2021-08-02**: First blueprint version 🎉 needs Home Assistant Core 2021.7 or higher for Trigger_ID to work.
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.md#contacts).

Why do I need this?

> This functionality started as a way to help my Bedroom AC unit keep an even temperature throughout the bedroom over night. My partner wanted the fan on, but not faster than it had to be. I wanted it to change speeds following the temperature of the room. So that's what I did.
>
> I continue to use this functionality in a slightly different way in my home system. If you want to see my use the automation form of this look at my [HA Configuration GitHub repository](https://github.com/SirGoodenough/Home-Assistant-Config). You will see that I have combined the control of the AC unit climate entity with this fan speed function and also have an 'on demand' version of this for when the room needs to be used during the day. My feeling was that I wanted to make this accessible to a wider audience, so I created this blueprint.
>
> If you are looking to tweak the function here or are looking for something the same but different, hit me up on my [Discord](https://discord.gg/Uhmhu3B) and we can work on that! If you see problems or have questions and don't want to use Discord, Comments here are also welcome.
>

## 🔧 Configuration

Requirements

* 1 input_boolean entity as the feature so you can enable or disable the automation easily. [![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)
* 1 input_number used as the target temperature for the area you will be in.
* 1 temperature sensor or temp average sensor or filtered temp sensor. This should be located physically within the breeze area of the fan for maximum desired affect.

## 🗂 Input fields

    people2monitor/name: Person or People to follow
        Select the Person you want this BP to trigger 
        on for this action. Multiples are allowed.

    fan_control/name: Toggle to turn the fan function off for when away or seasonally
        (#1) ```input_boolean``` - If this is set to off, the Automation
        will be disabled.

    room_temp_now/name: Room Temperature Sensor
        (#2) This is a temperature sensor or averaged temperature sensor
        preferrably within the path of the moving air from the fan.

    room_set_temp/name: Room Target Temperature
        (#3) ```input_number``` - This is the target temperature of the
        room.

    temp_gap/name: Temp Hysteresis
        (#4) This keeps the fan from speed cycling too often. (Let''s
        call it Hysterisis)

    temp_gap_1_to_2/name: Temp Gap between Low and Medium
        (#5) This is the temp swing between Low and Medium.

    temp_gap_2_to_3/name: Temp Gap between Medium and High
        (#6) This is the temp change between Medium and High.

    fan_on_time/name: Time of day fan should start
        (#7) Set this for the time of day you want the fan function to
        be enabled.

    fan_off_time/name: Time of day fan should stop
        (#8) Set this for the time of day you want the fan function to
        end.

    weekday/name: Day of the week to use the Automation
        (#9) Enable it these days only

    loop_action/name: User action for fan enabled condition (loop)
        (#11) This is intended to start / set temp on an AC unit or whatever
        you want to do. It is executed on every successful trigger that does not send
        the operation to off.

    off_action/name: User action for fan off condition (off_action)
        (#12) This is intended to disable an AirCon unit or whatever you
        want to do. It is executed on every successful operation off trigger.

    **AutomationFanControl_HA_fan.yaml ONLY:**

    fan/name: Fan Entity
        (#10) This is the Home Assistant Fan entity

    **AutomationFanControl_MQTT.yaml ONLY:**

    mqtt_fan_topic/name: Fan Topic
        (#10) This is the MQTT Topic needed to change the fan speed.


## 👀 ✈️ Extended Information

Questions:

>  1. You can use either Metric or Imperial, but the sensor and the input_number have to be using the same scale.
>  2. The Hysteresis offset can be '0' for the simplest operation. If you hare using the input_number to control both this and a climate integration, you may want an offset so the fan does not quick cycle. It basically move the input_number set point by the amount you pick
>  3. You can have multiple automations running off of this with the same or different temp settings or times, but I suggest the times on 'ENABLED' versions do not overlap, or it will get very confused.

## 🛠 HOW the Blueprint / Automation works

Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. The Variables section has several entries. These are converting !inputs to variables that can be used in templates.
> 4. The triggers section has hooks for the listed things. 2 of them are used to stop the automation at the appropriate time, and the rest are used to start the automation or to adjust the fan speed on temperature changes.
> 5. In the action the first test looks to see if the automation wants to stop. If that is not the case, it will test the temperature reading against the set point and adjust the fan speed accordingly.
>

## 🪄 How do I use this

In the yaml file linked below I show how I and controlling my AirCon within the fan loop. I have a window unit that is WIFI enabled for Temperature and on/off. I set this up to only trigger to the AirCon unit when it actually needs to change something to avoid rate limiting situations. Follow the comments and see the [example yaml code here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/AutoFanControl_Aircon_Control_SAMPLE_Files.yaml)

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

Click this badge to import this Blueprint. This is the version that uses HA fan integration and 0%, 33%, 66%, & 100% values to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_HA_fan.yaml)

Click this badge to import this Blueprint. This is the version that uses MQTT speeds 0, 1, 2, 3 to control the fan:
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_MQTT.yaml)

Direct link to  download Blueprint:

HA Fan Entity Version: Version: Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_HA_fan.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_HA_fan.yaml

MQTT Version: Version: Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_MQTT.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl_MQTT.yaml


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