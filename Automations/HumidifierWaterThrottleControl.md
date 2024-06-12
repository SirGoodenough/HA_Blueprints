This blueprint monitors a humidity sensor & by determining the error from the goal, sends info to a humidifier as to how long to flow the water. This saves water & has a minimal effect on function. Requires a Sonoff SV, Generic hygrostat Integration, & a suitable humidifier.

## 📑 Changelog

* **2024-06-08**: Blueprint Input Sections for enhanced Descriptions.
* **2023-10-31**: Add Scalar to adjust the flow profile
* **2023-08-07**: Updates for Home Assistant 2023.8
* Selector syntax change
  * Condition Selector addition (where applicable)
  * MQTT Discovery name changes (where applicable)
  * Clean-up code formatting
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2023-02-92**: Add wait-to-send interrupt & new entity power_1
  * Fix extraction of current humidity
  * Comment out troubleshooting code
* **2023-01-30**: 🎉 First Release

<base target="_blank"\>

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.md#contacts).

Why do I need this?

> If you have an automatic humidifier on your central air heating system, you are likely wasting a lot of water. These systems often work by keeping some kind of wick wet and blowing some of the furnace air thru the wick, causing the water to evaporate and 'humidify' the house. The problem is that it likely turns the water on until the humidity is where it needs to be, then turns the water off. To be effective the wick needs to be wet. However if the water is applied 1/2 or 1/4 of the time, the wick will still be wet and effective, but you will use half or a quarter of the water that would have otherwise flowed passed the wick and down the drain.
>
> This Blueprint and system applies an intermittent stream of water to the humidifier allowing much less water to be flushed over the already wet wick and into the drain. Lower % humidity readings will cause the water stream to be on proportionally more. The closer to the target the less water is applied. These actions help keep the humidity more constant than the original controller.
>
> If you want to see my original install of this humidifier, I have a video you can watch. 
> 
[WhatAreWeFixing.Today Humidifier Video](https://whatarewefixing.today/77/episode-8-humidistat-replacement-using-home-assistant-and-tasmota-with-a-sonoff-sv/)
>
>This could, however, apply to any flow over wick humidifier by simply splitting the wires that go to the water valve and powering the water valve thru a sonoff SV running tasmota.

## 🔧 Configuration

Requirements

    Tasmota SV Device set-up to receive the output of this blueprint.
    Suitable Humidifier to control.

    Generic hygrostat integration or something similar. 
    [Link to sample Generic hygrostat config file](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/HumidifierWaterThrottleControl_SAMPLE.yaml)

## 🗂 Input fields

    humidifier ✯ REQUIRED ✯: Humidifier Entity
        This is the entity that represents the Generic hygrostat controlling
        the system.

    humidity ✯ REQUIRED ✯: Switch entity for switch 1 controlling the water
        This is the entity used by the blueprint and 
        Generic hygrostat to monitor the living area.

    mqtt_topic ✯ REQUIRED ✯: Topic to used send the time value to the Tasmota device
        A topic such as this with your device top topic. 
        We are setting var2 via cmnd: "cmnd/humidifier/var2" 
                See below for more details.

    power_1 ✯ REQUIRED ✯: I was finding that every time this BP updated the  
        Sonoff during the water on (delay command) stage, the sequence 
        stopped & the water time was cut short. To clean this up I added a 
        wait so that this BP only sends data when the water is not on. T
        hat wait is looking to the entity imported to HA when you built 
        the Sonoff SV switch to modulate the water output.

    scalar: Scaling Factor
        This number is the exponent in the calculation of how long the
        water stays on scaled against thd amount the actual humidity
        is below the target.

    minimum_time: Floor for time value sent to Tasmota
        Current default 20 seconds. Must be set lower than the 
        maximum time. This it the shortest time that will be sent to the 
        switch.

    maximum_time: Ceiling for time value sent to Tasmota
        Current default 80 seconds. Must be set higher than the 
        minimum time. This it the longest time that will be sent to the 
        switch. It is also used in the formula to calculate the time sent 
        to the switch.

    additional_conditions:
        Extra conditions you may want to add to this automation 
        (Example: Home occupied, TV on, etc)

## 👀 Where is My MQTT Topic?

This Blueprint needs to send the time value to var2 in your sonoff SV. On my system the MQTT topic to do this is ```cmnd/humidifier/var2```. Yours will be something similar. In order to determine exactly what your topic will be, follow these instructions.

Begin by opening the ```WEBUI``` of your Tasmota SV switch.

#### Select the Configuration tab

![Where is the Configuration TAB?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaConfig.png?raw=true "Where is the Configuration TAB?")

#### Select the MQTT tab

![Where is the Configure MQTT TAB?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaMQTT.png?raw=true "Where is the Configure MQTT TAB?")

#### Bottom of the screen is the topic

![Where is the TOPIC?](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaTopic.png?raw=true "Where is the TOPIC?")

## 🙊 How Do I Set-up My Sonoff SV?

#### Add a ghost relay & button as relay & button #2 in the Module Parameters screen & save it.

![Module Setup](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/tasmotaModuleSetup.png?raw=true "Module Setup")

#### Add the Rules

    Make sure you set all 3 rules to mode 4 after you load them.
    Rule1 4
    Rule2 4
    Rule3 4

    Also make sure you turn on the rules. Rule1 will turn on and off as 
    called in the program & is best starting as off.
    Rule1 0
    Rule2 1
    Rule3 1

    Full line of text versions of these rules are available in the Blueprint 
    Description. These are stacked for clarity.

Rule1 is turned on and off based on the status of Power2. When Rule1 is enabled it sets the 2 minute timer cycle and starts the Rule3 items on schedule. It sets variable 1 to the value of variable 2. Variable 2 is set via MQTT from the Blueprint.

```text
on Time#Minute|2 do var1 %var2% endon
```

Rule2 Provides set-up for boot and is the code for switching Rule1 on and off based on the status of Power2. Power1 is connected to the real relay and sends power to the water valve when on. Power2 (the ghost relay) is used by the Generic hygrostat to call for moisture or standby.

```text
on system#boot do backlog power2 0; var2 20 endon 
on POWER2#state=0 do backlog power1 0; rule1 0 endon 
on POWER2#state=1 do rule1 1 endon
```

Rule3 is the look-up table. It selects the delay time, which is the amount of time that the water cycles on within the 2 minute cycle based on the input on var2 from the blueprint. It has to be done this way because the Delay function in Tasmota does not accept a VARx value. Tasmota will test these from the top to the bottom and when it finds the first one that executes will end the line with a break and stop trying for more. It is a small footprint method of if/then coding. This table will allow water on times up to the full 120 seconds listed as a limit in the Blueprint.

```text
on var1#state>110 do backlog power1 on;delay 1200;power1 off break 
on var1#state>100 do backlog power1 on;delay 1100;power1 off break 
on var1#state>90 do backlog power1 on;delay 1000;power1 off break 
on var1#state>80 do backlog power1 on;delay 900;power1 off break 
on var1#state>70 do backlog power1 on;delay 800;power1 off break 
on var1#state>60 do backlog power1 on;delay 700;power1 off break 
on var1#state>50 do backlog power1 on;delay 600;power1 off break 
on var1#state>40 do backlog power1 on;delay 500;power1 off break 
on var1#state>30 do backlog power1 on;delay 400;power1 off break 
on var1#state>20 do backlog power1 on;delay 300;power1 off break 
on var1#state<=20 do backlog power1 on;delay 200;power1 off endon
```

## 📩 **Version Updates**

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

📩 There is not an official version control system for Blueprints. However I have found something that comes pretty close. It is not perfect, but for **MOST** Blueprints, it does just fine. I encourage you to check this script out and use it to easily check if I have updated this blueprint. [🔗koter84 Blueprint Update Script ](https://github.com/koter84/HomeAssistant_Blueprints_Update/)

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FHumidifierWaterThrottleControl.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/HumidifierWaterThrottleControl.yaml

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