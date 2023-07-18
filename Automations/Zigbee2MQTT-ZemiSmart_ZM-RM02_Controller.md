(18 actions!!) This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the 6 buttons of a ZemiSmart ZM-RM02 Controller. The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do. Functions that are left empty will simply do nothing. 

## 📑 Changelog

* **2023-07-17**: Adjust trigger-to statement
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaing you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions.
* **2022-04-17**: 🎉 🎛 🔋 New Blueprint!
<base target="_blank">


## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.md#contacts).

Why do I need this?

> This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the 6 buttons of a ZemiSmart ZM-RM02 Controller. The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do. Functions that are left empty will simply do nothing.

## 🔧 Configuration

Requirements

* My 'suggestion' is that you do separate scripts for most, if not all of the actions you generate here. If you are using the UI editor for the simple things you are fine, but for more complicated things scripts may work better for you. This is my opinion and how I am using it, to each their own. Building functions within the uI is also available if you are more comfortable with that.
* To make the Blueprint work you will need a functional RM02 integrated to Home Assistant thru Zigbee2MQTT and find the sensor entity in the Home Assistant Device tab that Z2M imported which is named similar this:
  + sensor.xxDevice_Namexx_action
  + [![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

If you do not see that sensor, 'LegacyAPI' might not be selected in the Zigbee2MQTT settings -  settings - advanced menu. Please find and check/select that setting like so:

![Z2M Menu Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-settings-advanced.png?raw=true "Where to find Z2M Legacy API Setting")

-- SCROLL DOWN --

![Legacy API Selected Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-legacy.png?raw=true "Where to find Z2M Legacy API Setting")



## 🗂 Input fields

    remote/name: Remote
        The entity to put here is the sensor that Z2M imported that is
        named like this ->  ```sensor.XXYour_HameXX_action```'

    tap_1:
      name: Single click on Button 1 action

    doubletap_1:
      name: Double click on Button 1 action

    hold_1:
      name: LongPress on Button 1 action

    tap_2:
      name: Single click on Button 2 action

    doubletap_2:
      name: Double click on Button 2 action

    hold_2:
      name: LongPress on Button 2 action

    tap_3:
      name: Single click on Button 3 action

    doubletap_3:
      name: Double click on Button 3 action

    hold_3:
      name: LongPress on Button 3 action

    tap_4:
      name: Single click on Button 4 action

    doubletap_4:
      name: Double click on Button 4 action

    hold_4:
      name: LongPress on Button 4 action

    tap_5:
      name: Single click on Button 5 action

    doubletap_5:
      name: Double click on Button 5 action

    hold_5:
      name: LongPress on Button 5 action

    tap_6:
      name: Single click on Button 6 action

    doubletap_6:
      name: Double click on Button 6 action

    hold_6:
      name: LongPress on Button 6 action

## 🔧 It won't work.. Are my Button presses working?

There is sample code to make the template sensor in the help file on GitHub Repo.

Within this blueprint there is an event handler that will latch the last command that the blueprint finds and sends that to the event buss. From there a simple Template sensor can grab it and show you the last action sent. This will help when setting up new functions and to troubleshoot strange behaviors. Add an entity card in your dashboard for sensor.cube_last_action to see what actions occur as you press the buttons.

[Yaml file that contains the sample code here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/RM02_Last_Action_Template_Trigger_SAMPLE.yaml)

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-ZemiSmart_ZM-RM02_Controller.yaml

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