These are several Script Blueprints written to help other Automations or Blueprints complete repetitive ot tricky tasks.

## 📑 Changelog

* **2023-12-07**: Stop log spamming leak. [#32](https://github.com/SirGoodenough/HA_Blueprints/issues/32)
* **2023-11-14**: Add Transition to Dimmer as per FR [#24](https://github.com/SirGoodenough/HA_Blueprints/issues/24)
* **2023-08-07**: First release as it's own Blueprint Exchange thread 🎉

<base target="_blank"\>

## 🔮 About this blueprint

Type of blueprint: SCRIPT

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Tasmota_EZ-Buttons.md#contacts).

Why do I need this?

> There are several Script Blueprints in here. The Descriptions provided should help you decide if you need them in your life or not.
> Several of these are designed to accept a number from 0 to 360 like the angle number that comes out of a Aqara Xiaomi Magic Cube's angle value and do something with it. There are others as well that do other things.

## 🔃 Device Reset

This script was invented to be used with my Device Tracker-Monitor-Notifier Blueprint. I released it as a standalone Script Blueprint because I saw an opportunity to add another tool to my toolbox, and possibly to others
toolboxes.

There are other places in my HA config where I need to reset something and now I can use this thing.

It asks for the entity or list of entities that you want to reset and how long you want them to be off for the reset.

When a Script using this Blueprint is called, it will use Homeassistant turn off to shut them off, wait the delay, then turn them back on. Simple Simple, but if you are doing it over and over in an automation, this cleans up the code quite a bit.

### 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fdevice_reset.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/device_reset.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/device_reset.yaml.

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 🔊 Volume Control 4 Magic Cube

This script was invented to be used with my Magic Cube Blueprints. I released it as a standalone Script Blueprint because because of requests to extend the function of my BP's with how to convert cube rotation to volume in other places. Research found me this [Post from Petro](https://community.home-assistant.io/t/cant-seem-to-set-volume-level-based-on-itself-from-data-template/237089/11?u=sir_goodenough) which had a very elegant solution to the problem, It was very easy decision to adopt it here.

To use this blueprint, install it from the source in the normal way. After that add your unique name for the Script, and add an icon and change the entity_id if desired.

You should only need to run the blueprint once, as you will be calling the unique name/entity you added above to use the code and provide action data. This script has one !input in the Blueprint screen to set the sensitivity of the rotation to volume changes. 30 seemed about right, but adjust as
needed.

Because all the data is added to control the action live at each use this is the only !input. This requires you call this generated script wth 2 data values when you want it to run. One is a positive or negative number between 360 and -360 that in the original, represents the input angle from the cube movement. The other data point is the entity of the media_player that you are trying to control.

**NOTE:*** the trigger variable below will be different for Z2M and ZHA and others. Look at my documentation for that cube integration help if you need it.

Sample call / use of this script for ZHA:

```yaml
- service: script.cube_dimmer_control_bp
    data:
    angle: '{{ trigger.event.data.args.relative_degrees | default(0.1) | float(0.2) }}'
    mp: media_player.farg
```

Sample call / use of this script for Z2M:

```yaml
- service: script.cube_dimmer_control_bp
    data:
    angle: '{{ trigger.payload_json.action_angle | default(0.1) | float(0.2) }}'
    mp: media_player.farg
```

### 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fvolume_control_4_magic_cube.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/volume_control_4_magic_cube.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/volume_control_4_magic_cube.yaml.

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 🌈 Color Control 4 Magic Cube

This script was invented to be used with my Magic Cube Blueprints. I released it as a standalone Script Blueprint because I saw others struggling with how so convert cube rotation to light dimming in other places.


To use this blueprint, install it from the source in the normal way. After that add your unique name for the Script, and add an icon and change the entity_id if desired.

You should only need to run the blueprint once, as you will be calling the unique name/entity you added above to use the code. This script has 1 input to select the relationship between the rotation amount and the speed of the color change.

This requires you call this script wth 3 data values. One is a positive or negative number between 360 and -360 that in the original, represents the input angle from the cube movement. The second data point is the entity of the light or light group that you are trying to control. The third is to tell the BP id you are controlling the red, the blue, or the green part of the color.

***NOTE:*** the trigger variable below will be different for Z2M and ZHA and others. Look at my documentation for that cube integration help if you need it.

Sample call / use of this script with ZHA:

```yaml
- service: script.cube_color_control
    data:
    angle: '{{ trigger.event.data.args.relative_degrees | default(0.1) | float(0.2) }}'
    light: light.grp_studio
    t_color: red
```

Sample call / use of this script with Z2M:

```yaml
- service: script.cube_color_control
    data:
    '{{ trigger.payload_json.action_angle | default(0.1) | float(0.2) }}'
    light: light.kitchensink
    t_color: red
```

### 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fcolor_control_4_magic_cube.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/color_control_4_magic_cube.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/color_control_4_magic_cube.yaml.

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 🌗 Dimmer Control 4 Magic Cube

This script was invented to be used with my Magic Cube Blueprints. I released it as a standalone Script Blueprint because I saw others struggling with how so convert cube rotation to light dimming in other places.

To use this blueprint, install it from the source in the normal way. After that add your unique name for the Script, and add an icon and change the entity_id if desired.

You should only need to run the blueprint once, as you will be calling the unique name/entity you added above to use the code. This script has 2 inputs in the Blueprint screen to set the sensitivity of the rotation action and the minimum brightness level for your lights. If the rotation is too sensitive the lights will change from dim to bright
in too short of a rotation so make it less sensitive. If the lights flicker at low brightness, raise the minimum brightness level to stop it.

The data is sent to the generated script to control the action live at each use. You only need to execute this blueprint generator script if you wish to change in input values or create another dimmer script.

There is a third optional field available, transition. This is the transition value for the lights. It can be picked as a field, as an input, or ignored. Ignored it doesn't change the current value in the light. If you call the script with a data field that has priority and that will be the value set. If there is no data field called, and there is an input value, that will be used.

This requires you call this script wth 2 data values. One is a positive or negative number between 360 and -360 that in the original, represents the input angle from the cube movement. The other data point is the entity of
the light or light group that you are trying to control.

***NOTE:*** the trigger variable below will be different for Z2M and ZHA and others. Look at my documentation for that cube integration help if you need it.

Sample call / use of this script for ZHA:

```yaml
- service: script.cube_dimmer_control_bp
    data:
    angle: '{{ trigger.event.data.args.relative_degrees | default(0.1) | float(0.2) }}'
    light: light.grp_studio
    transition: 4
```

Sample call / use of this script for Z2M:

```yaml
- service: script.cube_dimmer_control_bp
    data:
    angle: '{{ trigger.payload_json.action_angle | default(0.1) | float(0.2) }}'
    light: light.grp_kitch
```
### 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fdimmer_control_4_magic_cube.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/dimmer_control_4_magic_cube.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/dimmer_control_4_magic_cube.yaml.

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 🎏 Long Short Toggle 4 Magic Cube

This script was invented to be used with my Magic Cube Blueprints. I released it as a standalone Script Blueprint because I saw others struggling with how so convert cube rotation to actions in other places.

To use this blueprint, install it from the source in the normal way. After that add your unique name for the Script, and add an icon and change the entity_id if desired.

You should only need to run the blueprint once, as you will be calling the unique name/entity you added above to use the code. This script has no inputs in the Blueprint screen because all the data is added to control the action live at each use.

This requires you call this script with a couple of data values. One is a positive or negative number between 360 and -360 that in the original, represents the input angle from the cube movement. The other data point is the entity of the device(s) that you are trying to control. Only 1 of the short_entity or long_entity is required 4 this
Blueprint to work.

***NOTE:*** the trigger variable below will be different for Z2M and ZHA and others. Look at my documentation for that cube integration help if you need it.

Sample call / use of this script with ZHA:

```yaml
- service: script.cube_long_short_toggle
    data:
    angle: '{{ trigger.event.data.args.relative_degrees | default(0.1) | float(0.2) }}'
    short_entity: light.kitchen_down_lights
    long_entity: light.kitchensink
```

Sample call / use of this script with Z2M:

```yaml
- service: script.cube_long_short_toggle
    data:
    angle: '{{ trigger.payload_json.action_angle | default(0.1) | float(0.2) }}'
    short_entity: light.kitchen_down_lights
    long_entity: light.kitchensink
```

### 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Flong_short_toggle_4_magic_cube.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/long_short_toggle_4_magic_cube.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/long_short_toggle_4_magic_cube.yaml.

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 📩 **Version Updates**

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

📩 There is not an official version control system for Blueprints. However I have found something that comes pretty close. It is not perfect, but for **MOST** Blueprints, it does just fine. I encourage you to check this script out and use it to easily check if I have updated this blueprint. [🔗koter84 Blueprint Update Script ](https://github.com/koter84/HomeAssistant_Blueprints_Update/)

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