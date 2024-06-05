(Hundreds of possible actions!!) Works with MQTT Directly bypassing both Legacy and non-Legacy trigger issues. Uses a Zigbee2MQTT built MQTT sensor to sort out the 38(+54) commands available from the Xiaomi Magic Cube. This gives you the ability to trigger actions using the remote. NOTICE: Using this Blueprint and example scripts, this cube *can* be triggered many ways, but only 38(+54) of them are unique...

## 📑 Changelog

* **2024-06-02**: Blueprint Input Sections for enhanced Descriptions.
* **2023-12-09**: Stop log spamming leak. [#32](https://github.com/SirGoodenough/HA_Blueprints/issues/32)
* **2023-10-20**: Enhancement [Add flip to side from any](https://github.com/SirGoodenough/HA_Blueprints/issues/22)
* **2023-08-07**: Updates for Home Assistant 2023.8
  * LOOK [THIS LINK](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Update_Instructions/Update--Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.md) FOR IMPORTANT UPDATE INSTRUCTIONS
  * Selector syntax change
  * Condition Selector addition (where applicable)
  * MQTT Discovery name changes (where applicable)
  * Clean-up code formatting
* **2022-03-01-A**: Beef-up the note not to use spaces and non alpha in MQTT topics.
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-28**: Code cleanup.
  * Add note to fix configuration conflict template error:
  * Update angle configuration text to help with config errors. No Code Change.
  *  **Error while executing automation automation.friendly_name_automations: TemplateError: Must provide a device or entity ID**
* **2022-12-22**: Change instances of the attribute ```angle``` to ```action_angle``` to fix non-legacy bug.
  * Add note not to use spaces and non alpha in MQTT topics.
* **2022-12-12**: Add Update Method Note, minor code change.
  * Name of Blueprint may have changed meaning you have to re-download with a new link.
  * If name changed, it is similar. Variables have not changed.
* **2022-12-04**: Re-did the backend to use MQTT instead of the Z2M Legacy configuration.
  * This removes the legacy trigger requirement and makes it respond much faster.
  * Old version Deprecated and available on the original Github link but will be no longer supported.
  * Old Github link still works if you need it for something...
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions plus shortcut or.
* **2022-04-26 update-B**: UPDATE: No code changes. Added examples to provide another 30 more ways to trigger something using conditionals in Group 3 🍐,
* **2022-04-26 update-A** UPDATE: No code changes. Added examples to provide 24 more ways to trigger something using the rotate sensor as a device toggle, both long and short for each rotate sensor.
* **2022-04-26**: Re-configure to add 30 Action Methods !!NOTICE!! If you are upgrading the Blueprint, upgrade the template sensor as well. The variables are different...
  * Add 30 flip actions for any side to any side addressing
  * Add 'last_side' variable to display sensor and code
  * Change variable named 'event' into 'action' fo clarity
  * Change variable named 'sub-event' into 'side' for clarity
  * dded Group 1 🍎, Group 2 🍒, & Group 3 🍐 to help users decide which sensors to populate
  * Added Emojis to help people visualize what action is in what Group
* **2022-04-11**: No Code Change. Added guidance to solve missing Action Sensor condition in this document.
  * Example code bug fix from [Michael Fischer](https://community.home-assistant.io/u/DagobahMike)
* **2022-03-17**: Added 6 functions that do not care about side. Makes it simple if you only want a couple of functions.
  * Added some aliases on some choose statements to improve Trace Diagrams and Troubleshooting.
* **2022-03-12**: Changed de-bounce logic from not repeating the last action to single mode and added a 1 second delay at the end. Was hard to do the same action twice (IE: Rotation) as the logic would prevent it.
* **2022-02-15.1**: Later that same day realized that if you have more than 1 cube, the event will be lacking so added ID.
* **2022-02-15**: 🎉 Forked from https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006 Version 1.2
  * Updated Documentation.
  * Added Latched event sensor.

<base target="_blank"\>

## 🔧 * Hardware Versions

Aqara / Lumi has released a new version of the cube. Box name listed as Cube T1 Pro. This Blueprint is NOT for that cube. It will work, sorta, but you will be missing Functions. Please see [this Blueprint](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Aqara-Magic-Cube-T1-Pro-CTP-R01-Xiaomi-Lumi.md) to configure that version of the cube.

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.md#contacts).

Why do I need this?

> The Cube remote/switch device has a lot of ways to trigger it. This Blueprint makes it a bit easier to figure out what you are doing and remembering that in the future. It also makes sure the trigger is as clean and repeatable as possible, screening out false triggers and making the log clean and the experience good overall.

## 🔧 Configuration

Requirements

* To make the Blueprint work you will need a functional Magic Cube integrated to Home Assistant thru Zigbee2MQTT.
* My 'suggestion' is that you do separate scripts for most, if not all of the actions you generate here. If you are using the UI editor for the simple things you are fine, but for more complicated things scripts may work better for you. This is my opinion and how I am using it, to each their own. See my example dimmer script below...
* IF YOU SEE --> TemplateError: Must provide a device or entity ID   ... 
  + If you get an error like that, The friendly_name in Z2M likely does not match the friendly_name on HA. To fix go into the Z2M ```Open web UI``` and set the  friendly_name there. Setting this in just HA or in Z2M without ticking the update HA box will cause this.
* This version of the Blueprint uses MQTT to deal with cube interface duties. This means that if you have Legacy triggers enabled on your setup or not, it will still work. It also created it's own number helper to track a variable needed to do all the tricks. You as the user will not have to deal with that.

You will also need the correct MQTT topic to talk to your device.

##### This blueprint has been known to freak out when there are spaces or odd characters in the MQTT Topic. Make sure there are no spaces, ONLY a single word, and ONLY A thru Z, a thru z, and 0 thru 9 in the topic. (```  /  ``` is ok between device and topic) If there are, you will need to change the name of the cube to remove those characters.

>> Wise advice from: [HiveMQ](https://www.hivemq.com/blog/mqtt-essentials-part-5-mqtt-topics-best-practices/):
>>
>> ### Never use spaces in a topic
>>
>> A space is the natural enemy of every programmer. When things are not going the way they should, spaces make it much harder to read and debug topics. Just because something is allowed, doesn’t mean it should be used. UTF-8 has many different white space types, such uncommon characters should be avoided.
>>
>> ### Use only ASCII characters, avoid punctuation and non printable characters
>>
>> Because non-ASCII UTF-8 characters often display incorrectly, it is very difficult to find typos or issues related to the character set. Unless it is absolutely necessary, we recommend avoiding the use of non-ASCII characters in a topic.

The topic can be found by going into devices and finding your cube device. [![Open your Home Assistant instance and show your devices.](https://my.home-assistant.io/badges/devices.svg)](https://my.home-assistant.io/redirect/devices/)

![Find Device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/FindDevice.png?raw=true "Find Device")

Then clicking on ```MQTT INFO```:

![Click MQTT INFO](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/MQTTInfo.png?raw=true "Click MQTT INFO")

Then looking for the subscribed topic that looks like this... ```zigbee2nqtt/[your device name here]```:

![Find the subscribed topic](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/MQTTTopic.png?raw=true "Find the subscribed topic")

That is what belongs in the the topic question you get when setting up a new automation with this blueprint.

## 🪲 Template error

If you see an error similar to: **Error while executing automation automation.magic_cube_automations: TemplateError: Must provide a device or entity ID** there is a way to fix it. It happens (usually) because the friendly_name that is in HA does not match the friendly_name that is in Z2M.
In order to fix I suggest you go into the Z2M web UI and change the friendly name. Below is how to do this if you are using the Z2M Addon.

1. Open the Z2M Web UI:
![Open the Z2M Web UI](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-WebUI.png?raw=true)

2: Select the change name icon in the row of the cube device:
![Select the change namr icon in the row of the cube device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-ChangeName.png?raw=true)

3: Change the name and be certain to tick the box to update HA at the same time:
![Change the name and be certain to tick the box to update HA at the same time](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2M-Devicename.png?raw=true)

After this find the topic again the same way as above and it should work.

## 🗂 Input fields

    topic/name: Topic
        The main MQTT Topic for your cube. 

    additional_conditions:
        Extra conditions you may want to add to this automation 
        (Example: Home occupied, TV on, etc)
______________

    shake:
      name: Shake the cube 🍕 Group 4
        This trigger only occurs once in the set-up.
        It can be combined in any group.'

    drop:
      name: Drop the cube 🍕 Group 4
        **NOTE: NOT available with the ```Cube T1 Pro``` version of the cube!!**
        This trigger only occurs once in the set-up.
        It can be combined in any group.'
______________

    slide_any:
      name: Group 2 actions 🍒 Slide the cube with any side

    doubletap_any:
      name: Group 2 actions 🍒 Double tap the cube with any side

    flipped90_any:
      name: Group 2 actions 🍒 Flip the cube 90 degrees to any side

    flipped180_any:
      name: Group 2 actions 🍒 Flip the cube 180 degrees any side

    rotate_cw_any:
      name: Group 2 actions 🍒 Rotate cube clockwise with any side

    rotate_ccw_any:
      name: Group 2 actions 🍒 Rotate cube counter clockwise with any side
______________

    **There is a set of these 🍎 for all 6 sides. 36 inputs total..**

    slide_face_0:
      name: Group 1 actions 🍎 Slide the cube with face 0 up

    doubletap_face_0:
      name: Group 1 actions 🍎 Double tap the cube with face 0 up

    flipped90_face_0:
      name: Group 1 actions 🍎 Flip the cube 90 degrees to face 0

    flipped180_face_0:
      name: Group 1 actions 🍎 Flip the cube 180 degrees to face 0

    flip_from_any_to_face_0:
      name: Group 1 actions 🍎 Flip the cube from any to face 0

    rotate_cw_face_0:
      name: Group 1 actions 🍎 Rotate cube clockwise with face 0 up

    rotate_ccw_face_0:
      name: Group 1 actions 🍎 Rotate cube counter clockwise with face 0 up
______________

    **There is a set of these 🍐 for all 6 sides. 30 inputs total..**
    
    0_from_1:
      name: Group 3 actions 🍐 Flip the cube to side 0 from side 1

    0_from_2:
      name: Group 3 actions 🍐 Flip the cube to side 0 from side 2

    0_from_3:
      name: Group 3 actions 🍐 Flip the cube to side 0 from side 3

    0_from_4:
      name: Group 3 actions 🍐 Flip the cube to side 0 from side 4

    0_from_5:
      name: Group 3 actions 🍐 Flip the cube to side 0 from side 5

## 👀 ✈️ Extended Information

This Blueprint uses a Zigbee2MQTT built sensor to sort out the commands available from the Xiaomi Magic Cube Remote. 

The split out of functions gives you the ability to assign local scripts or functions
to do the things you want the remote to do.

Functions that are left empty will simply do nothing.

### 🍎 There is a set of 36 event functions that will trigger on specific actions
on specific sides that are listed as **Group 1 actions 🍎**.

### 🍒 There is a set of 6 event functions that will trigger on specific actions
on *ANY* side that are listed as **Group 2 sctions 🍒**.

### 🍐 There is a set of 30 event functions that will trigger on cube flips to
& froma specific sides that are listed as **Group 3 sctions 🍐**.

### 🍕 There are 2 actions (shake and drop) that only occur once and are OK to
be combined with any other group. Listed as **Group 4 sections 🍕**.

Please be aware that ALL actions except the 2 listed above,

🍕 will trigger an action in **ALL 3 groups at the same time** every time. Therefore
I suggest if you just have a couple of things you want this remote to do that
you choose the *ANY / Group 2 / 🍒* events.

If you want more than a few events, you should select actions in **Group 1 / 🍎
OR Group 3 / 🍐**.

With careful selection you can use mixed groups, but you run the risk of a single
cube action triggering more than 1 Home Assistant action and making a mess of
things 🍱.

## 🪄 My Cube triggers on the Desk with a slight Bump. How do I fix that?

I have 3 of these cubes. If you aren't careful they trigger and do all kinds of things just sitting on the desk. Awesome when you want it to do this, but a HUGE PITA if you don't.

A friend of mine came up with this and it works awesome. He didn't want people hassling him about remixes and such, so he let me put it on the Thingiverse. I printed one for each of my cubes and because it's now parked at a diagonal it will not trigger, unless you knock it on the floor or something. I highly suggest you print yourself one of these or find someone to print one for you.... It will make cube life much simpler...
https://www.thingiverse.com/thing:4536778

#### NOTICE: This cube *can* be triggered over a hundred ways, but only 38 of them are unique

## 🔧 How does this darn cube work?

There is sample code to make the template sensor in the help file on GitHib named the same as this one and in the community page related to this.

#### Seeing the cube commands for training the operator

Within this blueprint there is an event handler that will latch the last command that the blueprint finds and sends that to the event buss. From there a simple Template sensor can grab it and show you the last action sent. This will help when setting up new functions and to troubleshoot strange behaviors. Add an entity card in your dashboard for sensor.cube_last_action to see what actions occur as you move the cube.

[Yaml file that contains the sample code here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Cube_Last_Action_Template_Trigger_SAMPLE.yaml)

#### Event Sensor in Action

![Sample Script Generation Dashboard Entry](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/cubesensor.gif?raw=true "Sensor in action")

If you wish to 'store' these events you can add this sensor to recorder and it will save them for you.

## 🫳 Getting Tap and Flip actions to work

I have had reports of the 'tap' action working. It was due to the lack of instructions provided by the manufacturer of the cube. Tap actions on the cube are initiated by sharply tapping the cube 2x on a hard surface like this:

![Demo of Tap Action](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Tap_Action.gif?raw=true "Demo of Tap Action")

In a similar manner, flips need to tap the surface at the end of the 90 or 180 flip. Setting up the template sensor above will help train you in the force needed for all the actions.

## 🙊 Acknowledgments

> This was 'forked' from 
>> [Aqara Cube ZHA - Simplified face-based device control](https://community.home-assistant.io/t/aqara-cube-zha-simplified-face-based-device-control/388850)
> Project authored by EdwardTFN (Edward Firmo) and he based on on several other giants that came up with most of the base code.
>>
>> [ZHA - Aqara Magic Cube (57 actions)](https://community.home-assistant.io/t/zha-aqara-magic-cube-57-actions/297012)
>>
>> [Aqara Magic Cube ZHA (51 actions)](https://community.home-assistant.io/t/aqara-magic-cube-zha-51-actions/270829)
>>
>> [ZHA - Aqara Magic Cube (24 actions)](https://community.home-assistant.io/t/zha-aqara-magic-cube-24-actions/377162)
>
>I sincerely thank Them for their work. 
I wanted to support a version that was virtually the same as my Z2M version, 
and leverage all the documentation and code samples there but still port it 
to ZHA. I also had a better idea for troubleshooting info.

## 🌞 Dimmer Control

If you are looking for a dimmer control to change brightness based on rotation, here's something I cobbled together from other community posts here and there. ( Credit https://community.home-assistant.io/u/yourigh/summary and others )

I did this with all the complicated stuff in a script that is called with data from the blueprint automation. Then the complicated part is all in 1 place and there is only 1 copy of it. The same script works for both increase and decrease of brightness because the angle in the cube goes positive when turning clockwise and negative when going counter clockwise.

[Code Examples are found in the Yaml file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Z2M_Cube_Dimmer_Control_Stub_Actions_and_Script_SAMPLE.yaml)
If you want to create the script file using a script BluePrint, I have that for you right here: [Dimmer Control BluePrint](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/dimmer_control_4_magic_cube.yaml)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fdimmer_control_4_magic_cube.yaml)

* The script reduces the angle number to 40% of the rotation angle (you can change this, but 40% works well for my needs).
* It then grabs the current brightness from the light entity (as a % of the full scale 255 number).
* The new_brightness target is then calculated.
* It then checks if the light is already off, and if so, leaves it off.
* It makes sure the new_brightness is above, in my case, 10% so all the lights come on.
* It then makes sure that if new_brightness >90%, it is set to 100% and not over that.
* Finally it provides the calculated brightness %.

#### NOTICE when building action scripts...

It has been found that some set-ups use ```trigger.payload_json.action_angle``` here and others only accept ```trigger.payload_json.angle``` here. I have not been able to determine which attributes are available in which version of firmware and/or configurations, so it is up to you to determine the one you need here. Look in the Device listing for this cube and determine which version of angle is one of the listed sensors. That would be the one to use here.

## 🚦 Color Control

I also extended this to controlling the color one octet (color) at a time. Each color will use both rotations on one side of the cube. Colors are changed one at a time (Red or Green or Blue) and change the amount (positive ot negative) based on how far you rotate the cube.

[Code Examples are found in the Yaml file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Z2M_Cube_Color_Control_Stub_Actions_and_Script_SAMPLE.yaml)
If you want to create the color change script file using a script BluePrint, I have that for you right here: [Color Change BluePrint](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/color_control_4_magic_cube.yaml)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fcolor_control_4_magic_cube.yaml)

* The script reduces the angle number to 60% of the rotation angle (you can change this, but 60% works well for my needs).
* It then grabs the current colors from the light entity and puts them into a list.
* The new color target is then calculated.
* It makes sure the new color is not negative.
* It then makes sure that the new color is not over 255.
* Finally it provides the calculated color if not in the limits.

This can be used over and over for as many lights as you want to control. But you **will** need to repeat this and modify it for red and blue color octets.

#### NOTICE when building action scripts...

It has been found that some set-ups use ```trigger.payload_json.action_angle``` here and others only accept ```trigger.payload_json.angle``` here. I have not been able to determine which attributes are available in which version of firmware and/or configurations, so it is up to you to determine the one you need here. Look in the Device listing for this cube and determine which version of angle is one of the listed sensors. That would be the one to use here.

## 🔁 🔴 Using Rotate CW and CCW as a Short-Press / Long-Press Toggle

Not enough switch positions for you?  **How about a possible 24 more?**  I came up with some scripts you can add to Home Assistant and call for more actions. One is for CW rotation < 100 degrees, another for > 100 degrees. Also the same for CCW. These are can be called from the Group 1 🍎 rotate actions and the Group 2 🍒 rotate actions. Match the CW call/recieve or the CCW call/receive pairs together or you are going to be sad. 😩

Here is a sample of what you put into the script Blueprint UI. It will need to be a manual YAML edit and contain your specific variables. What you see here is one from my config.

[Code Examples are found in the Yaml file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Z2M_Cube_Rotate_Long_and_Short_press_SAMPLE.yaml)
If you want to create the long / short rotation switch script file using a script BluePrint, I have that for you right here: [Long Short Rotation Switch BluePrint](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/long_short_toggle_4_magic_cube.yaml)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Flong_short_toggle_4_magic_cube.yaml)

You can also do this buy going full gui and picking the matching template out of the below section and filling it in similar to this:

![Full GUI Example](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/full_GUI_Example.png?raw=true "Full GUI Example")

This is a [homeassistant.toggle action](https://www.home-assistant.io/integrations/homeassistant#service-homeassistanttoggle), so it can toggle anything that that service can handle. Changing it to homeassistant.turn_on or homeassistant.turn_off would change the behavior slightly if this fits your needs better. Using this integration, you can control lights, switches, locks, and lots of different things.

#### NOTICE when building action scripts...

It has been found that some set-ups use ```trigger.payload_json.action_angle``` here and others only accept ```trigger.payload_json.angle``` here. I have not been able to determine which attributes are available in which version of firmware and/or configurations, so it is up to you to determine the one you need here. Look in the Device listing for this cube and determine which version of angle is one of the listed sensors. That would be the one to use here.

## 🎧 Volume Control

This script was invented to be used with my Magic Cube Blueprints. I released it as a standalone Script Blueprint because because of requests to extend the function of my BP's with how to convert cube rotation to volume in other places. Research found me this [Post from Petro](https://community.home-assistant.io/t/cant-seem-to-set-volume-level-based-on-itself-from-data-template/237089/11?u=sir_goodenough) which had a very elegant solution to the problem, It was very easy decision to adopt it here.

[Code Examples are found in the Yaml file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/ZHA_Cube_Volume_Control_Stub_Actions_and_Script_SAMPLE.yaml)
If you want to create the script file using a script BluePrint, I have that for you right here: [Volume Control BluePrint](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/volume_control_4_magic_cube.yaml)
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Fvolume_control_4_magic_cube.yaml)

* The script scales the angle number of the rotation angle (you can change this, but 30 works well for my needs).
* You send the script the media_player that you want to adjust.
* You use a template (examples in the script BP description) to send the angle to the script.
* Some math happens and it uses the amount you turn the cube to adjust the volume.

#### NOTICE when building action scripts...

It has been found that some set-ups use ```trigger.payload_json.action_angle``` here and others only accept ```trigger.payload_json.angle``` here. I have not been able to determine which attributes are available in which version of firmware and/or configurations, so it is up to you to determine the one you need here. Look in the Device listing for this cube and determine which version of angle is one of the listed sensors. That would be the one to use here.

## Method to use Group 3 🍐 actions and not interfere with Group 1 🍎

Not enough switch positions for you still?  **How about another posible 30 more?** 

This is another 'action' that I stumbled upon. I noticed if you turn the cube from side to side very gently, it will internally register as being on a new side, but the flip action doesn't register. Then if you slide the cube, it will send out an action of slide on side 5 from side 2, or whatever side combo's you choose. I used 5 from 2 in the example, but you can use any of them.

![Showing slide 5 from 2 on the Cube Action Sensor](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Slide5From2.png?raw=true "Showing slide 5 from 2 on the Cube Action Sensor")

I'll be honest, this is the trickiest thing to do yet and I'm not sure it is worth the trouble, but if you want an action in your pocket as a secret action that only you know, this is the trick. Using a soft surface like a towel helps to keep the flip from registering when you set it down.

> NOTE: In this example the slide side 5 will also trigger. You may need to add a condition to prevent that from triggering. An example for this 5 from 2 example is to put this condition on the slide side 5 action ```{{ not last_side == 2 }}``` before the thing you want to do. Or you can just not have a slide 5 action.

It is as simple as adding a condition of let's say 'slide' in one of the Group 3 🍐 slots.

Here is the GUI editor showing this.

![Full GUI Example Conditional side to side](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/conditionalSide2Side.png?raw=true "Full GUI Example conditional side to side")

[Code Examples are found in the Yaml file here](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Samples/Cube_Secret_Additional_commands_SAMPLE.yaml)

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

# Please Click the 🧡 at the end of this top Post if you find this Useful

## 📲 **Software to Download** 💾

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml)

Direct link to download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT-Xiaomi_Cube_Controller_MQTT_Triggered.yaml.

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