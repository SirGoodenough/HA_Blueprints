(74 actions!!) This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38 commands available from the Xiaomi Magic Cube. This gives you the ability to trigger actions using the remote. NOTICE: Using this Blueprint, this cube *can* be triggered 74 ways, but only 38 of them are unique...

## 📑 Changelog

* **2022-04-26**: Re-configure to add 30 Action Methods
  * Add 30 flip actions for any sode to any side addressing
  * Add 'last_side' variable to display sensor and code
  * Change variable named 'event' into 'action' fo clarity
  * Change variable named 'sub-event' into 'side' for clarity
  * Added Group 1 🍎, Group 2 🍊, & Group 3 🍐 to help users decide which sensors to populate
  * Added Emojis to help people visualize what action is in what Group
* **2022-04-11**: No Code Change.  Added guidance to solve missing Action Sensor condition in this document.
  * Example code bug fix from [Michael Fischer](https://community.home-assistant.io/u/DagobahMike)
* **2022-03-17**: Added 6 functions that do not care about side.  Makes it simple if you only want a couple of functions.
  * Added some aliases on some choose statements to improve Trace Diagrams and Troubleshooting.
* **2022-03-12**: Changed debounce logic from not repeating the last action to single mode and added a 1 second delay at the end.  Was hard to do the same action twice (IE: Rotation) as the logic would prevent it.
* **2022-02-15.1**: Later that same day realized that if you have more than 1 cube, the event will be lacking so added ID.
* **2022-02-15**: Forked from https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006 Version 1.2
  * Updated Documentation.
  * Added Latched event sensor.

## 📩 Get Started

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

I have 2 of these cubes. If you aren't careful they trigger and do all kinds of things just sitting on the desk. Awesome when you want it to do this, but a HUGE PITA if you don't.

A friend of mine came up with this and it works awesome. He didn't want people hassling him about remixes and such, so he let me put it on the Thingiverse. I printed one for each of my cubes and because it's now parked at a diagonal it will not trigger, unless you knock it on the floor or something. I highly suggest you print yourself one of these or find someone to print one for you.... It will make cube life much simpler...
https://www.thingiverse.com/thing:4536778

### Option 1: My Home Assistant

Click the badge to import this Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZigbee2MQTT%2520-%2520Xiaomi%2520Cube%2520Controller.yaml)

# Please Click the 🧡 at the end of this Top Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.yaml

## 📖 Description

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38 commands available from the Xiaomi Magic Cube Remote. The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do. Functions that are left empty will simply do nothing.  

### 🍎 There is a set of 36 event functions that will trigger on specific actions on specific sides that are listed as **Group 1 actions 🍎**

### 🍊 There is a set of 6 event functions that will trigger on specific actions on *ANY* side that are listed as **Group 2 sctions 🍊**

### 🍐 There is a set of 30 event functions that will trigger on cube flips to & froma specific sides that are listed as **Group 3 sctions 🍐**

### 🍩 There are 2 actions (shake and drop) that only occur once and are OK to be combined with any other group

Please be aware that ALL actions except the 2 listed above / 🍩 will trigger an action in **ALL 3 groups at the same time** every time. Therefore I suggest if you just have a couple of things you want this remote to do that you choose the *ANY / Group 2 / 🍊* events. If you want more than a few events, you should select actions in **Group 1 / 🍎 OR Group 3 / 🍐**. With careful selection you can use mixed groups, but you run the risk of a single cube action triggering more than 1 Home Assistant action and making a mess of things 🍱.  

#### NOTICE: This cube *can* be triggered 74 ways, but only 38 of them are unique

There is sample code to make the template sensor in the help file on GitHib named the same as this one and in the community page related to this.

Within this blueprint there is an event handler that will latch the last command that the blueprint finds and sends that to the event buss. From there a simple Template sensor can grab it and show you the last action sent. Thie will help when setting up new functions and to troubleshoot strange behaviours.

```yaml
template:
  - trigger:
    - platform: event
      event_type: cube_last_action
  sensor:
    - name: "Cube Last Action"
      unique_id: Any-unique-string-here-MUST-be-unique
      icon: mdi:eye-refresh-outline
      attributes:
        friendly_name: "Cube Action"
      state: >
        {{ trigger.event.data.friendly_name }} - 
        {{ trigger.event.data.action }} - 
        {{ trigger.event.data.side }} frm 
        {{ trigger.event.data.last_side }}
```

Event Sensor in Action:
![Sample Script Generation Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/cubesensor.gif?raw=true "New sensor compared to the visual display of the action sensor")

If you wish to 'store' these events you can add this sensor to recorder and it will save them for you.

My 'suggestion' is that you do separate scripts for most, if not all of the actions you generate here. If you are using the UI editor for the simple things you are fine, but for more complicated things scripts may work better for you. This is my opinion and how I am using it, to each their own.  See my example dimmer script below...

_________________________

> This was 'forked' from 'https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006'
V1.2 project authored by luckypoppy and the friends he pulled together to create the base.  
>
> I sincerely thank Him (Them) for their work. I felt there needed to be more documentation for rookie users to properly set this up. I had quite a few questions and when I saw a few questions in that chat from people struggling, I wanted to help. I also had a better idea for troubleshooting info.

_________________________

First, let’s go over Blueprints and what they are. Blueprints are a way to share automations and is built into Home Assistant. Simple as that. You can import my template code and a copy of it will reside in your configuration. Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build an automation. It will collect the information needed based on your entities and your personal adjustments, and provide a working automation. You will have to have or add the required hardware and entities that the Blueprint needs to function.

### ⚙️ Usage

#### 🛠 Installation

* Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
* Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
* In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:

> ◦ https://github.com/SirGoodenough/HA_Blueprints

#### 🧬 To make the blueprint work it will need

To make the Blueprint work you will need a functional Magic Cube integrated to Home Assistant thri Zigbee2MQTT and find the sensor entity in the Home Assistant Device tab that Z2M imported which is named similar this:

* sensor.xxDevice_Namexx_action

If you do not see that sensor, 'LegacyAPI' might not be selected in the Zigbee2MQTT settings -  settings - advanced menu. Please find and check/select that setting like so:

![Z2M Menu Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-settings-advanced.png?raw=true "Where to find Z2M Legacy API Setting")

-- SCROLL DOWN --

![Legacy API Selected Screen](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-legacy.png?raw=true "Where to find Z2M Legacy API Setting")

The other 4 imported sensors in this Device can be disabled as they will not be used.

Once you have found the entity_id you can build the Automation. To build the automation:

> 1. Click on 'Create Automation'  [![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/) and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes

## 🌞 Dimmer Control

If you are looking for a dimmer control to change brightness based on rotation, here's something I cobbled together from other community posts here and there. ( Credit https://community.home-assistant.io/u/yourigh/summary and others )

I did this with all the complicated stuff in a script that is called with data from the blueprint automation. Then the complicated part is all in 1 place and there is only 1 copy of it. The same script works for both increase and decrease of brightness because the angle in the cube goes positive when turning clockwise and negative when going counter clockwise.

In the blueprint automation:

```yaml
rotate_cw_face_0:
  - service: script.cube_dimmer_control
    data:
      angle: "{{ trigger.to_state.attributes.action_angle }}"
      light: light.bulb1
rotate_ccw_face_0:
  - service: script.cube_dimmer_control
    data:
      angle: "{{ trigger.to_state.attributes.action_angle }}"
      light: light.bulb1
```

Then this is the script that's called to do the heavy lifting.   It works for both CW and CCW cube rotations.

In the script intrgration:

```yaml
cube_dimmer_control:
  description: Template Dimmer Control
  variables:
    angle:
    light:
  sequence:
    - service: light.turn_on
      data_template:
        entity_id: "{{ light }}"
        brightness_pct: >
          {% set step_size = angle * 0.4 %}
            {# Get brightness as a percent. #}
          {% set cb = (state_attr( light, 'brightness') | float(10) / 255.0) * 100.0 %}
          {% set new_brightness = cb | int(10) + step_size %}
          {% if new_brightness < 5 %}
            {# If it gets really low set to 0. Adjust if needed for your lights. #}
            0
          {% elif new_brightness <= 10 %}
            {# If it's not quite 0, set to a minimum working brightness. #}
            10
          {% elif 91 <= new_brightness < (90 + step_size) %}
            {# If it's almost full brightness, set to 100%. #}
            100
          {% else %}
            {# Send actual calculated value. #}
            {{ new_brightness }}
          {% endif %}
```

* The script reduces the angle number to 40% of the rotation angle (you can change this, but 40% works well for my needs).
* It then grabs the current brightness from the light entity (as a % of the full scale 255 number).
* The new_brightness target is then calculated.
* It then checks if the light is already off, and if so, leaves it off.
* It makes sure the new_brightness is above, in my case, 10% so all the lights come on.
* It then makes sure that if new_brightness >90%, it is set to 100% and not over that.
* Finally it provides the calculated brightness %.

## 🚦 Color Control

I also extended this to controlling the color one octet (color) at a time. Each color will use both rotations on one sude of the cube.  Colors are changed one at a time (Red or Green or Blue) and change the amount (positive ot negative) based on how far you rotate the cube.

In the blueprint automation:

```yaml
## Side 5 green
rotate_cw_face_5:
  - service: script.cube_green_color_control
    data:
      angle: "{{ trigger.to_state.attributes.action_angle }}"
      light: light.grp_studio
rotate_ccw_face_5:
  - service: script.cube_green_color_control
    data:
      angle: "{{ trigger.to_state.attributes.action_angle }}"
      light: light.grp_studio
```

Then this is the script that's called to do the heavy lifting. It works for both CW and CCW cube rotations.

In the Script Intrgration:

```yaml
cube_green_color_control:
  description: Control the green part of the color
  variables:
    light:
    angle:
  sequence:
    - service: light.turn_on
      data_template:
        entity_id: "{{ light }}"
        rgb_color: >
          {% set step_size = angle * 0.6 %}
          {% set color = state_attr(light, 'rgb_color') %}
          {% set R = color[0] %}
          {% set G = color[1] %}
          {% set B = color[2] %}
          {% set new_green = G + step_size | int(0) %}
          {% if new_green < 0 %}
            {# Make sure it doesn't go negative #}
            {{ R, 0, B }}
          {% elif new_green > 255 %}
            {# Make sure it doesn't go over 255 #}
            {{ R, 255, B }}
          {% else %}
            {# Send the value calculated #}
            {{ R, new_green, B }}
          {% endif %}
```

* The script reduces the angle number to 60% of the rotation angle (you can change this, but 60% works well for my needs).
* It then grabs the current colors from the light entity and puts them into a list.
* The new color target is then calculated.
* It makes sure the new color is not negative.
* It then makes sure that the new color is not over 255.
* Finally it provides the calculated color if not in the limits.

This can be used over and over for as many lights as you want to control.  But you **will** need to repeat this and modify it for red and blue color octets.

# 🌐 All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

Here is a list of each of my blueprints, a quick description and jump links to the Blueprints Exchange post...

## 🌀 Scripts

#### 🧯Broadlink on Script Blueprint

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, Pushes remote buttons in sequence.

#### 🧯Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

#### 🧯Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean.

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

#### 🧯TTS All Message Blueprint

This script can use any of the 11 integrated TTS Platforms in Home Assistant to send a message to a media player.

https://community.home-assistant.io/t/tts-script-blueprint-for-all-11-ha-core-tts-flavors/400700

## 🔃 Automations

#### 🧯Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor.  Intended for Ifan03/Ifan04 but useful other places.

https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419

#### 🧯Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### 🧯Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the multitude of commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

#### 🧯Zigbee2MQTT - ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller.

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough