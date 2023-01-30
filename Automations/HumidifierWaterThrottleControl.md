



## 📑 Changelog

* **2023-01-30**: 🎉 First Release


:face_with_monocle: About this blueprint

Type of blueprint: AUTOMATION
What does it do?

This blueprint monitors a humidity sensor and by determining the error from the goal, sends info to a humidifier as to how long to modulate the water.  This saves water, and has a minimal effect on function.

## Configuration

Requirements

    Tasmota SV Device set-up to receive the output of this blueprint.
    Suitable Humidifier to control

## Input fields

    *humidifier :asterisk: REQUIRED:* This is the entity that represents the Generic hygrostat controlling the system.

    *humidity :asterisk: REQUIRED:* This is the entity used by the blueprint and Generic hygrostat to monitor the living area.

    *mqtt_topic :asterisk: REQUIRED:* A topic such as this with your device top topic. We are setting var2 via cmnd: ```cmnd/humidifier/var2``` 
                                    See below for more details.

    *minimum_time:* Current default 20 seconds. Must be set lower than the maximum time. This it the shortest time that will be sent to the switch.

    *maximum_time:* Current default 80 seconds. Must be set higher than the minimum time. This it the longest time that will be sent to the switch. It is also used in the formula to calculate the time sent to the switch.

## Where is My MQTT Topic?

The Blueprint needs to send the time value to var2 in your sonoff SV.  On my system the MQTT topic to do this is cmnd/humidifier/var2.  Yours will be something similar.  In order to determine exactly what your will be, follow these instructions.

#### Begin buy opening the webui of your Tasmotda SV switch


#### Select the Configuration tab


#### Select the MQTT tab


#### Bottom of the screen is the friendly_name and the topic


## How Do I Set-up My Sonoff SV?

#### Add a ghost relay and button as relay and button #2.


#### Add the Rles.

Rule1 is turned on and of based on the status of switch #2


Rule2 Provides set-up for boot and is the code for switching power1 on and off based on the status of power 2.  Power1 is connected to the real relay and sends power to the water valve.  Power2 is used by the Generic hygrostat to call for moisture or wait.


Rule3 is the look-up table.  It selects the delay time, which is the amount of time that the water cycles on within the 2 minute cycle based on the input on var2 from the blueprint.

:heavy_plus_sign: Other blueprints

    GitHub repo with all my blueprints (link)

:arrow_down: How to get this blueprint?

Click the badge to import this Blueprint (needs Home Assistant Core 2021.3 or higher):

Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.  (link)

Or you can also:

    Copy-paste the content from this link  (link) to a new file inside your configuration’s blueprint folder.

Changelog