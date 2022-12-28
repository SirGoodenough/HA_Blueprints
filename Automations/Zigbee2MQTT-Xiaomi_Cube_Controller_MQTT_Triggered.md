(128 possible actions!!) Works with MQTT Directly bypassing both Legacy and non-Legacy trigger issues. Uses a Zigbee2MQTT built MQTT sensor to sort out the 38(+54) commands available from the Xiaomi Magic Cube. This gives you the ability to trigger actions using the remote. NOTICE: Using this Blueprint and example scripts, this cube *can* be triggered 98 ways, but only 38(+54) of them are unique...

## 📑 Changelog

* **2022-12-28**: Code cleanup.
* * Add note to fix configuration conflict template error: 
* *  **Error while executing automation automation.friendly_name_automations: TemplateError: Must provide a device or entity ID**
* **2022-12-22**: Change instances of the attribute ```angle``` to ```action_angle``` to fix non-legacy bug.
* * Add note not to use spaces and non alpha in MQTT topics.
* **2022-12-12**: Add Update Method Note, minor code change.
* * Name of Blueprint may have changed meaning you have to re-download with a new link.
* * If name changed, it is similar. Variables have not changed.
* **2022-12-04**: Re-did the backend to use MQTT instead of the Z2M Legacy configuration.
* * This removes the legacy trigger requirement and makes it respond much faster.
* * Old version Deprecated and available on the original Github link but will be no longer supported.
* * Old Github link still works if you need it for something...
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions plus shortcut or.
* **2022-04-26 update-B**: UPDATE: No code changes. Added examples to provide another 30 more ways to trigger something using conditionals in Group 3 🍐,
* **2022-04-26 update-A** UPDATE: No code changes. Added examples to provide 24 more ways to trigger something using the rotate sensor as a device toggle, both long and short for each rotate sensor.
* **2022-04-26**: Re-configure to add 30 Action Methods !!NOTICE!! If you are upgrading the Blueprint, upgrade the template sensor as well.  The variables are different...
* * Add 30 flip actions for any side to any side addressing
* * Add 'last_side' variable to display sensor and code
* * Change variable named 'event' into 'action' fo clarity
* * Change variable named 'sub-event' into 'side' for clarity
* * dded Group 1 🍎, Group 2 🍊, & Group 3 🍐 to help users decide which sensors to populate
* * Added Emojis to help people visualize what action is in what Group
* **2022-04-11**: No Code Change.  Added guidance to solve missing Action Sensor condition in this document.
* * Example code bug fix from [Michael Fischer](https://community.home-assistant.io/u/DagobahMike)
* **2022-03-17**: Added 6 functions that do not care about side.  Makes it simple if you only want a couple of functions.
* * Added some aliases on some choose statements to improve Trace Diagrams and Troubleshooting.
* **2022-03-12**: Changed de-bounce logic from not repeating the last action to single mode and added a 1 second delay at the end.  Was hard to do the same action twice (IE: Rotation) as the logic would prevent it.
* **2022-02-15.1**: Later that same day realized that if you have more than 1 cube, the event will be lacking so added ID.
* **2022-02-15**: Forked from https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006 Version 1.2
* * pdated Documentation.
* * Added Latched event sensor.

## 📩 * Version Updates

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

🔗 There is not an official version control system for Blueprints.  However I have found something that comes pretty close.  It is not perfect, but for **MOST** Blueprints, it does just fine.  I encourage you to check this script out and use it to easily check if I have updated this blueprint.

[koter84 Blueprint Update Script](https://gist.github.com/koter84/86790850aa63354bda56d041de31dc70#file-readme-md)

## 📩 Get Started

Updates will be published on my [GIT repository](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

I have 2 of these cubes. If you aren't careful they trigger and do all kinds of things just sitting on the desk. Awesome when you want it to do this, but a HUGE PITA if you don't.

A friend of mine came up with this and it works awesome. He didn't want people hassling him about remixes and such, so he let me put it on the Thingiverse. I printed one for each of my cubes and because it's now parked at a diagonal it will not trigger, unless you knock it on the floor or something. I highly suggest you print yourself one of these or find someone to print one for you.... It will make cube life much simpler...
https://www.thingiverse.com/thing:4536778

### Option 1: My Home Assistant

Click the badge to import this Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml)

# Please Click the 🧡 at the end of the Top Post if you find this Useful

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml

## 📖 Description

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38 commands available from the Xiaomi Magic Cube Remote. The split out of functions gives you the ability to assign local scripts or functions to do the things you want the remote to do. Functions that are left empty will simply do nothing.  

### 🍎 There is a set of 36 event functions that will trigger on specific actions on specific sides that are listed as **Group 1 actions 🍎**

### 🍊 There is a set of 6 event functions that will trigger on specific actions on *ANY* side that are listed as **Group 2 actions 🍊**

### 🍐 There is a set of 30 event functions that will trigger on cube flips to & froma specific sides that are listed as **Group 3 actions 🍐**

### 🍩 There are 2 actions (shake and drop) that only occur once and are OK to be combined with any other group

Please be aware that ALL actions except the 2 listed above / 🍩 will trigger an action in **ALL 3 groups at the same time** every time. Therefore I suggest if you just have a couple of things you want this remote to do that you choose the *ANY / Group 2 / 🍊* events. If you want more than a few events, you should select actions in **Group 1 / 🍎 OR Group 3 / 🍐**. With careful selection you can use mixed groups, but you run the risk of a single cube action triggering more than 1 Home Assistant action and making a mess of things 🍱.  

#### NOTICE: This cube *can* be triggered 74+ ways, but only 38 of them are unique

### IF YOU SEE --> TemplateError: Must provide a device or entity ID

If you get an error like that, The friendly_name in Z2M likely does not match the 
friendly_name on HA. To fix go into the Z2M ```Open web UI``` and set the 
friendly_name there. Setting this in just HA or in Z2M without ticking the update HA
box will cause this.

There is sample code to make the template sensor in the help file on GitHib named the same as this one and in the community page related to this.

#### Seeing the cube commands for training the operator

Within this blueprint there is an event handler that will latch the last command that the blueprint finds and sends that to the event buss. From there a simple Template sensor can grab it and show you the last action sent. This will help when setting up new functions and to troubleshoot strange behaviors.  Add an entity card in your dashboard for sensor.cube_last_action to see what actions occur as you move the cube.

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

#### Event Sensor in Action

![Sample Script Generation Dashboard Entry](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/cubesensor.gif?raw=true "Sensor in action")

If you wish to 'store' these events you can add this sensor to recorder and it will save them for you.

#### Programming actions

My 'suggestion' is that you do separate scripts for most, if not all of the actions you generate here. If you are using the UI editor for the simple things you are fine, but for more complicated things scripts may work better for you. This is my opinion and how I am using it, to each their own.  See my example dimmer script below...

#### Getting Tap and Flip actions to work

I have had reports of the 'tap' action working.  It was due to the lack of instructions provided by the manufacturer of the cube.  Tap actions on the cube are initiated by sharply tapping the cube 2x on a hard surface like this:

![Demo of Tap Action](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Tap_Action.gif?raw=true "Demo of Tap Action")

In a similar manner, flips need to tap the surface at the end of the 90 or 180 flip.  Setting up the template sensor above will help train you in the force needed for all the actions.
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

To make the Blueprint work you will need a functional Magic Cube integrated to Home Assistant thru Zigbee2MQTT.

This version of the Blueprint uses MQTT to deal with cube interface duties.  This means that if you have Legacy triggers enabled on your setup or not, it will still work.  It also created it's own number helper to track a variable needed to do all the tricks.  You as the user will not have to deal with that.

You will also need the correct MQTT topic to talk to your device.

This blueprint has been known to freak out when there are spaces in the MQTT Topic.  Make sure there are no spaces and there are all ASCII characters in the topic, (```  /  ``` is ok)  
If there are, you will need to change the name of the cube to remove those characters.
>> Wise advice from: [HiveMQ](https://www.hivemq.com/blog/mqtt-essentials-part-5-mqtt-topics-best-practices/):
>>
>> ### Never use spaces in a topic
>>
>> A space is the natural enemy of every programmer. When things are not going the way they should, spaces make it much harder to read and debug topics. Just because something is allowed, doesn’t mean it should be used. UTF-8 has many different white space types, such uncommon characters should be avoided.
>>
>> ### Use only ASCII characters, avoid non printable characters
>>
>> Because non-ASCII UTF-8 characters often display incorrectly, it is very difficult to find typos or issues related to the character set. Unless it is absolutely necessary, we recommend avoiding the use of non-ASCII characters in a topic.

The topic can be found by going into devices and finding your cube device. [![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

![Find Device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/FindDevice.png?raw=true "Find Device")

Then clicking on ```MQTT INFO```:

![Click MQTT INFO](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/MQTTInfo.png?raw=true "Click MQTT INFO")

Then looking for the subscribed topic that looks like this... ```zigbee2nqtt/[your device name here]```:

![Find the subscribed topic](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/MQTTTopic.png?raw=true "Find the subscribed topic")

That is what belongs in the the topic question you get when setting up a new automation with this blueprint.

If you see an error similar to: **Error while executing automation automation.magic_cube_automations: TemplateError: Must provide a device or entity ID** there is a way to fix it.  It happens (usually) because the friendly_name that is in HA does not match the friendly_name that is in Z2M.
In order to fix I suggest you go into the Z2M web UI and change the friendly name.  Below is how to do this if you are using the Z2M Addon.

1. Open the Z2M Web UI:
![Open the Z2M Web UI](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-WebUI.png?raw=true)

2: Select the change name icon in the row of the cube device:
![Select the change namr icon in the row of the cube device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-ChangeName.png?raw=true)

3: Change the name and be certain to tick the box to update HA at the same time:
![Change the name and be certain to tick the box to update HA at the same time](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-Devicename.png?raw=true)

After this find the topic again the same way as above and it should work.

> 1. Click on 'Create Automation'  [![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/) and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes

Code Samples for the items in the next few sections can be found in my Home-Assistant Config here:  

* https://github.com/SirGoodenough/Home-Assistant-Config/blob/master/automation2/Z2M-Xiaomi_Cube_A2.yaml
* https://github.com/SirGoodenough/Home-Assistant-Config/blob/master/script2/cube_script.yaml

## 🌞 Dimmer Control

If you are looking for a dimmer control to change brightness based on rotation, here's something I cobbled together from other community posts here and there. ( Credit https://community.home-assistant.io/u/yourigh/summary and others )

I did this with all the complicated stuff in a script that is called with data from the blueprint automation. Then the complicated part is all in 1 place and there is only 1 copy of it. The same script works for both increase and decrease of brightness because the angle in the cube goes positive when turning clockwise and negative when going counter clockwise.

In the blueprint automation:
[![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/)

```yaml
rotate_cw_face_0:
  - service: script.cube_dimmer_control
    data:
      angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
      light: light.bulb1
rotate_ccw_face_0:
  - service: script.cube_dimmer_control
    data:
      angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
      light: light.bulb1
```

Then this is the script that's called to do the heavy lifting.   It works for both CW and CCW cube rotations.

In the script integration:
[![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)

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

I also extended this to controlling the color one octet (color) at a time. Each color will use both rotations on one side of the cube.  Colors are changed one at a time (Red or Green or Blue) and change the amount (positive ot negative) based on how far you rotate the cube.

In the blueprint automation:
[![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/)

```yaml
## Side 5 green
rotate_cw_face_5:
  - service: script.cube_green_color_control
    data:
      angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
      light: light.grp_studio
rotate_ccw_face_5:
  - service: script.cube_green_color_control
    data:
      angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
      light: light.grp_studio
```

Then this is the script that's called to do the heavy lifting. It works for both CW and CCW cube rotations.

In the Script Integration:
[![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/)

```yaml
cube_green_color_control:
  description: Control the green part of the color
  variables:
    light:
    angle:
  sequence:
    - service: light.turn_on
      data:
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

## 🔁 🔴 Using Rotate CW and CCW as a Short-Press / Long-Press Toggle

Not enough switch positions for you?  **How about a possible 24 more?**  I came up with some scripts you can add to Home Assistant and call for more actions.  One is for CW rotation < 100 degrees, another for > 100 degrees.  Also the same for CCW.  These are can be called from the Group 1 🍎 rotate actions and the Group 2 🍊 rotate actions.  Match the CW call/receive or the CCW call/receive pairs together or you are going to be sad. 😩

Here is a sample of what you put into the script Blueprint UI.  It will need to be a manual YAML edit and contain your specific variables.  What you see here is one from my config.

```yaml
service: script.cube_long_cw_toggle
data:
  angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
  entity: light.livingroomlight
```

And if you are editing it manually in an editor inside the Script calling yaml, this is the way it should look for rotate ce face 3, as an example.

```yaml
rotate_cw_face_3:
  - service: cube_long_cw_toggle
    data:
      angle: '{{ trigger.payload_json.action_angle | float(0.0)}}'
      entity: light.livingroomlight
```

You can also do this buy going full gui and picking the matching template out of the below section and filling it in similar to this:

![Full GUI Example](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/full_GUI_Example.png?raw=true "Full GUI Example")

These are the standalone scripts that are 'called' from the Script calling yaml shown above.  If you don't need all of these only install the ones you will use.

This is a [homeassistant.toggle action](https://www.home-assistant.io/integrations/homeassistant#service-homeassistanttoggle), so it can toggle anything that that service can handle.  Changing it to homeassistant.turn_on or homeassistant.turn_off would change the behavior slightly if this fits your needs better.  Using this integration, you can control lights, switches, locks, and lots of different things.

```yaml
script:
cube_short_cw_toggle:
  description: CW Short Press Toggle
  variables:
    entity:
    angle:
  sequence:
    - condition: template
      value_template: '{{ angle > 0 <= 100 }}'
    - service: homeassistant.toggle
      target:
        entity_id: '{{ entity }}'
cube_long_cw_toggle:
  description: CW Long Press Toggle
  variables:
    entity:
    angle:
  sequence:
    - condition: template
      value_template: '{{ angle > 100 }}'
    - service: homeassistant.toggle
      target:
        entity_id: '{{ entity }}'

cube_short_ccw_toggle:
  description: CCW Short Press Toggle
  variables:
    entity:
    angle:
  sequence:
    - condition: template
      value_template: '{{ angle < 0 >= -100 }}'
    - service: homeassistant.toggle
      target:
        entity_id: '{{ entity }}'
cube_long_ccw_toggle:
  description: CCW Long Press Toggle
  variables:
    entity:
    angle:
  sequence:
    - condition: template
      value_template: '{{ angle < -100 }}'
    - service: homeassistant.toggle
      target:
        entity_id: '{{ entity }}'
```

## Method to use Group 3 🍐 actions and not interfere with Group 1 🍎

Not enough switch positions for you still?  **How about another posible 30 more?** 

This is another 'action' that I stumbled upon.  I noticed if you turn the cube from side to side very gently, it will internally register as being on a new side, but the flip action doesn't register.  Then if you slide the cube, it will send out an action of slide on side 5 from side 2, or whatever side combo's you choose.  I used 5 from 2 in the example, but you can use any of them.

![Showing slide 5 from 2 on the Cube Action Sensor](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Slide5From2.png?raw=true "Showing slide 5 from 2 on the Cube Action Sensor")

I'll be honest, this is the trickiest thing to do yet and I'm not sure it is worth the trouble, but if you want an action in your pocket as a secret action that only you know, this is the trick.  Using a soft surface like a towel helps to keep the flip from registering when you set it down.

> NOTE: In this example the slide side 5 will also trigger. You may need to add a condition to prevent that from triggering. An example for this 5 from 2 example is to put this condition on the slide side 5 action ```{{ not last_side == 2 }}``` before the thing you want to do.  Or you can just not have a slide 5 action.

It is as simple as adding a condition of let's say 'slide' in one of the Group 3 🍐 slots.

Here is the GUI editor showing this.

![Full GUI Example Conditional side to side](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/conditionalSide2Side.png?raw=true "Full GUI Example conditional side to side")

Here is the YAML editor showing this:

```yaml
alias: Aqara Magic Cube test
description: stuff happens here
use_blueprint:
  path: SirGoodenough/Zigbee2MQTT - Xiaomi Cube Controller MQTT Triggered.yaml
  input:
    remote: sensor.yertle_action
    5_from_2:
      - condition: template
        value_template: '{{ action == "slide" }}'
      - service: light.toggle
        data: {}
        target:
          entity_id: light.kitchensink
```

## 🌞 ❄️ Troubleshooting tip

If you are troubleshooting and you want to see more traces back when doing so, here is a TIP I've found.
Manually edit the automation created with the ui editor (or manually with a text editor) and add the following to have this automation contain 10 traces instead of the normal 5.  Then if the automation is triggering often, you can see the last 10 traces to help you decide what the issue is.

```yaml
alias: aaaaaaa Test
description: 'See how to increase the number of Traces available''
trace:
  stored_traces: 10
use_blueprint:
.....
```

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

This Blueprint is for controlling a 3 speed fan based on a temperature sensor. Both fan % control & MQTT fan control versions.

https://community.home-assistant.io/t/auto-fan-temp-control-for-3-speed-fan-using-ha-fan-or-mqtt-integration/326419

#### 🧯Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### 🧯Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385

#### 🧯Zigbee2MQTT - Xiaomi Cube Controller Blueprint

This Blueprint uses a Zigbee2MQTT built sensor to sort out the 38(+54) commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zigbee2mqtt-xiaomi-cube-controller/393203

#### 🧯Zigbee2MQTT - ZemiSmart ZM-RM02 Controller Blueprint

This Blueprint uses the Z2M (Zigbee2MQTT) imported Action sensor to sort out the 18 commands from the ZemiSmart ZM-RM02 Controller.

https://community.home-assistant.io/t/zigbee2mqtt-zemismart-zm-rm02-controller/412650

#### 🧯ZHA - Xiaomi Cube Controller Blueprint

This Blueprint uses a ZHA built sensor to sort out the 38(+54) commands from the Xiaomi Magic Cube Remote.  

https://community.home-assistant.io/t/zha-xiaomi-cube-controller/495975

#### 🧯Device_tracker Monitor & Notifier

This Blueprint Monitor's device_tracker entities that you choose & notifies you if they go offline. Then it gives you the opportunity to devise an action to deal with it.

https://community.home-assistant.io/t/device-tracker-monitor-notifier/500688

## 🤹🏾‍♂️ Contact Links or see my other work

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## 🧀 If you want to support me

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough