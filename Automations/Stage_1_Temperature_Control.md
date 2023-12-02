This is Blueprint will adjust your climate entity thermostat to 1° above the current temp and keep it there until a max temp. This keeps my stage 2 heat source off during chosen times. Only runs within the time period you state. There isd also facility to control based on zone occumation and a roll-your-own reason.

## 📑 Changelog

* **2023-12-02**:  🎉 First release!
<base target="_blank">

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Person_Alert_Blueprint.md#contacts).

Why do I need this?

> I use this BluePrint to set my Pellet stove on in the morning without triggering my stage 2 oil furnace. Without this when the thermostat setbaco adjust from the overniight 55° setting to the morning 70 degree setting, the jump of more than 2° between actual and set forced the oil stove to start.  Using this, only the wood burns.
>
> I set this up to use the current temperature ans the temperature set point in e standard climate entity. You may have to adjust things if you want to run it different.
>[![Open your Home Assistant instance and show an integration.](https://my.home-assistant.io/badges/integration.svg)](https://my.home-assistant.io/redirect/integration/?domain=climate)
>
> There is an optional ability, defaulting to false (off), to prevent the BluePrint from triggering should a zone you pick be unoddupied.
> [HA ZONES LINK](https://www.home-assistant.io/integrations/zone/)
> [![Open your Home Assistant instance and show your zones.](https://my.home-assistant.io/badges/zones.svg)](https://my.home-assistant.io/redirect/zones/)
>

## 🔧 Configuration

Requirements

* An HA climate entity that can monitor temperature and provide the current_temperature be the entity to be controlled.

## 🗂 Input fields

    people2monitor/name: Person or People to follow
        Select the Person you want this BP to trigger 
        on for this action. Multiples are allowed.

    climate_e/name: Room Thermostat
        The Climate device, thermostat, that you are ramping.

    maxTemp/name: Goal Temperature
        If it is at least this, go no warmer.

    rampRate/name: Degrees above actual
        Keep set point this above actual

    interval/ name: Hold Period
        Set this delay between thermostat temp setting events.
        If it changes the goal set temp, it waits this long before it rechecks.
        Basically this rate limits stuff.

    ramp_start_time/name: Time of day ramp should start
        Set this for the time of day you want the ramp function to be enabled.

    weekday/name: Day of the week to use the Automation
        Control temp on these days with this automation.

    occ_test/name: Enable the Occupancy test?
        This BluePrind can take into consideration if a zone is occupied.
        To enable this feature, select yes.
        To ignore this feature select no.

    t_zone/name: Zone to monitor for occupancy
        If you said yes above, then you enter the zome to monitoe here.
        Default zone is home. Change to another zone if you want to.
        If you said no above, this section has no effect on your BluePrint.

    additional_conditions/name: Additional conditions
        Extra conditions you may want to add to this automation 
        (Example: It is the heating season, etc.)

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FPerson_Alert_Blueprint.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Person_Alert_Blueprint.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Person_Alert_Blueprint.yaml

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