This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean. Think a lock from a common keypad, or a puzzle to solve in a safe house. 
ALSO you can watch the accompanying [YouTube Video](https://youtu.be/ZILTAZQPr_Q) about it here for detailed info!

## 📑 Changelog

* **2024-06-08**: Blueprint Input Sections for enhanced Descriptions.
* **2023-08-07**: Updates for Home Assistant 2023.8
  * Selector syntax change
  * Condition Selector addition (where applicable)
  * MQTT Discovery name changes (where applicable)
  * Clean-up code formatting
* **2023-03-01**: Add Author Tag. Bump HA required Version to 2023-3-0
* **2022-12-12**: Add Update Method Note, minor code change.
  * Name of Blueprint may have changed meaing you have to re-download with a new link.
  * If name changed, it is similar. Variables have not changed.
* **2022-05-05**: Updated for 2022.5.0 HA. Added Markdown to !input Descriptions plus shortcut and.
* **2021-11-20**: Add Minimum Home Assistant version.
* **2021-09-03**: Add Description.
* **2021-08-04**: Add comments and cleanup.
* **2021-07-21**: Add the watchdog timeout test.
* **2021-07-11**: First blueprint version 🎉 Needs Home Assistant Core 2021.7 or higher for Trigger_ID to work

<base target="_blank"\>

## 🔮 About this blueprint

Type of blueprint: AUTOMATION

What if I am having problems getting it going?

> You can contact me for help, [see the links below](https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.md#contacts).

Why do I need this?

> This all started out with my <a href="https://whatarewefixing.today/125/tasmota-based-drop-pin-door-lock/" target="_blank">Less Than $30 Drop Pin Lock</a> Project that I installed a couple of years ago in my house. These locks had the unfortunate problem of not having a way to unlock them from the outside without Google Home or the Home Assistant App on your phone. I always wanted to create a keypad that would function in this manner, and until the addition of the Trigger_ID feature in Home Assistant 2021.7, the Automation while possible, would involve extensive use of complicated templating that I was not in the mood to build. Trigger_ID’s made it simple!

## 🔧 Configuration

Requirements

* 5 binary_sensor entities to sense the button presses
* 1 input_boolean entity as the feature to trigger the lock action  [![Open your Home Assistant instance and show your helper entities.](https://my.home-assistant.io/badges/helpers.svg)](https://my.home-assistant.io/redirect/helpers/)
* 1 input_number entity to store the internal sequence number

## 🗂 Input fields

    people2monitor/name: Person or People to follow
        Select the Person you want this BP to trigger 
        on for this action. Multiples are allowed.

    button_one/name: Button Press One
        ```Binary Sensor``` for First Button Pressed'

    button_two/name: Button Press Two
        ```Binary Sensor``` for Second Button Pressed'

    button_three/name: Button Press Three
        ```Binary Sensor``` for Third Button Pressed'

    button_four/name: Button Press Four
        ```Binary Sensor``` for Forth Button Pressed'

    button_five/name: Button Press Five
        ```Binary Sensor``` for Fifth Button Pressed'

    lock_control/name: Buffer for the Final Lock Enable
        ```input_boolean``` - Final Enable to trigger
        your lock or action'

    seq_status/name: Control Sequence Status Placeholder
        ```input_number``` - The internal use lock
        sequence number (set range to 0 to 100)
        You will need one of these for every copy of
        this automation, IE one for every lock code.

    on_timer/name: Lock On Time in Seconds
        Time output signal is on in seconds.
        Generally 5 seconds is good here.

    additional_conditions:
        Extra conditions you may want to add to this automation 
        (Example: Home occupied, TV on, etc)

## 👀 ✈️ Extended Information

> The binary sensors can be the inputs from a device like I have OR it can be existing devices. For instance if you want to walk into your back porch and use the PIR as button one, then in sequence you trigger the freezer door, the light switch on the wall, the doorbell, and the fridge door, then that can be your door unlock sequence. No keypad needed! 
> 
> I personally bought an RM433 from Itead / Sonoff and plugged the number codes into my RF-Bridge set-up and went with that.
>
> 1. Click on 'Create Automation'  [![Open your Home Assistant instance and show your automations.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/) and 'Use Blueprint'
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes
> 4. Select a Lock On time in seconds. This is how long the input_boolean stays on before the lock is released.
> 5. Test that your Cipher works by pressing the buttons and watching the result.

## 🧬 Walk-thru:

> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. In the Variables section has several entries. The first is needed to convert the !input: variable of the input_number into a variable so that it can be used in a template. After that we grab and store the last time the sequence number was changed, the actual value of the sequence number, and the current time. These are used for the watchdog so that the code cannot be accidentally left ‘almost’ triggered.
> 4. In the trigger section there is a trigger for each button, watching for that button to be pressed. When the button is pressed, a trigger_id is generated and passed along to the action: section so it knows which trigger was initiated.
> 5. In the action: section the always executed first part is the watchdog. It checks that the last time the sequence number was changed was within the last 5 minutes. Otherwise if the sequence was left at the 4th button for a week, all someone would have to do it hit the 5th button and it would open the lock.
The rest is one big choose: statement. To get button 1 to be accepted you only need the button 1 trigger_ID and this changes the sequence code number. In order to get to stage 2 of the cipher, both the trigger_ID and the sequence number have to be correct, and once it is, it again changes the sequence number. This pattern is repeated until the fifth number is pressed with the correct sequence code set and that fires the input_boolean to open the lock. Should you press the numbers in the wrong order, the cipher resets and you need to know to start over. Pressing button 1 again will also reset the sequence via the default action in the choose code.

## 🪄 How do I get my lock open?

I have created a sample script as one possible example of how to do this.

To get your lock to open, build a simple automation using the UI (or manually) that triggers on your input boolean, and the action is opening your lock or whatever you want to do. For example:

```yaml
  - id: 0b408ade-16fd-42fc-8333-518660b421ae
    mode: single
    max_exceeded: silent
    alias: test lock
    initial_state: on
    trigger:
      - platform: state
        entity_id: input_boolean.pad_enable
    action:
      - service: lock.unlock
        data:
          code: '7554288'
        target:
          entity_id: lock.side_door
```

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

HA link to download blueprint: [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2Fkeypad_5_button_cipher_to_turn_on_something.yaml)

Direct link to  download Blueprint: ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/keypad_5_button_cipher_to_turn_on_something.yaml


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