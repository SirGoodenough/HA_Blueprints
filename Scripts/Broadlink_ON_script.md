This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, IE: antenna, FireTV, Chromecast, etc. The defaults are specific to me and you should change them to match your situation.

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
* **2022-04-11**: Add multiple to Entity Selections and changed minimum HA to 2022.4.0
* **2021-11-20**: Changes because of release of Blueprint Script UI
  * Add Minimum Home Assistant 2021-11-0
* **2021-09-14**: First blueprint version 🎉
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: SCRIPT

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.md#contacts).

Why do I need this?

> This is a Script Blueprint that takes on the huge mess of scripts created by the Standard Broadlink Integration and script sequences them into functions. IE: 'Turn on my Chromecast' or 'Start music on my receiver'
> 
> If you have a Broadlink that helps run your TV, you know exactly what I mean about a mess. Every button and function and button sequence on your remote becomes another script that must be called to get stuff done. It's hard enough to remember what button does what on the remote itself, remembering all the names of the buttons it impossible (for me).
>
> The scripts built with this Blueprint gives you a common scenario for turning your stuff on and putting the device in the correct mode to do the things you want to do. It's called programmed macros or the like on some remotes. I have a number instances of this blueprint script created in my system. Here is a shot of them:
>
> ![My Buttons in Lovelace](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Screenshot_2022-01-08_20-11-15.png?raw=true "Examples of this Blueprint in Lovelace")

## 🔧 Configuration

Requirements

* Broadlink Integration happy and running in Home Assistant.
* The remote buttons that you plan on using stored in HA as scripts ready to call.
* An HA Dashboard set-up to store, present, and keep track of your Broadlink scripts.

## 🗂 Input fields

    adapter_power:/name: Turn on the smart plug that powers the adapter
        This is the switch entity for the device that powers the streaming device.
        I have my Chromecast & Firestick connected thru a smart plug.

    reciever_power:/name: Reciever Power
        This is a call to the script that turns the Reciever Device ON.

    tv_power:/name: TV Power
        This is a call to the script that turns on the TV Entity.

    tv_mode:/name: TV Input Mode
        This is a call to the script to select the feed into the TV. 

    tv_ota_mode:/name: OTA Input Mode
      description: 
        This is a call to the script to select the Over The Air TV mode to put 
          the TV Mode into a known state. 
        Note- My TV uses multiple presses to select some inputs, 
          so this is needed in my case. You may not need this.
          Adjust sequence accordingly...

    reciever_input:/name: Reciever Input
        This is a call to the script that turns the Receiver
          Input to the correct adapter line

    reciever_out_mode:/name: Reciever Speaker Out Mode
        This is a call to the script that turns the Reciever
          Speakers into the desired output mode

    cooldown:/name: Cooldown
        The delay between IR Blasts...
          My Broadlink sends stuff out faster than my equipment
          can respond, so this gaps the commands.

## 👀 ✈️ Extended Information

For further information, reference these links.

>      https://www.home-assistant.io/integrations/broadlink/
>      https://www.home-assistant.io/docs/automation/using_blueprints/
>      [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)

## 💡 Other Thoughts

This was set-up specifically for my instance and configured for my hardware. Chances of you plugging this in as defaulted and it working for you are low. My hope here is that you take what I am using anf adjust the BP main body script to do that you want it to do. Since I don't have your hardware, this will need to be something that you do, but if you get stuck or want advice, look at the bottom of this post / file for contact info and contact me directly.

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FBroadlink_ON_script.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml

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