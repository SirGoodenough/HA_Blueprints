This Blueprint is for controlling a 3 speed fan based on a temperature sensor.  Intended for Ifan03/Ifan04 but useful other places.

## :arrow_down: Get Started

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint (needs Home Assistant Core 2021.7 or higher for Trigger_ID to work)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FAutoFanControl.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.yaml

## :page_facing_up: Description

This functionality started as a way to help my Bedroom AC unit keep an even temperature throughout the bedroom over night.  My partner wanted the fan on, but not faster than it had to be.  I wanted it to change speeds following the temperature of the room.  So that's what I did.

I continue to use this functionality in a slightly different way in my home system.  If you want to see my use the automation form of this look at my [HA Configuration GitHub repository](https://github.com/SirGoodenough/Home-Assistant-Config).  You will see that I have combined the control of the AC unit climate entity with this fan speed function and also have an 'on demand' version of this for when the room needs to be used during the day.  My feeling was that I wanted to make this accessible to a wider audience, so I created this blueprint.

If you are looking to tweak the function here or are looking for something the same but different, hit me up on my Discord  (https://discord.gg/Uhmhu3B) and we can work on that!  If you see problems or have questions and don't want to use Discord, Comments here are also welcome.

First, let’s go over Blueprints and what they are.  Blueprints are a way to share automations and is built into Home Assistant.  Simple as that.  You can import my template code and a copy of it will reside in your configuration.  Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build an automation.  It will collect the information needed based on your entities and your personal adjustments, and provide a working automation.  You will have to have or add the required hardware and entities that the Blueprint needs to function.

### How the Blueprint works:

To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public REPO on GitHub:
>  ◦   ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/AutoFanControl.yaml```

To make the blueprint work it will need:
> • 1 input_boolean entity as the feature so you can enable or disable the automation easily
> • 1 input_number used as the target temperature for the area you will be in
> • 1 temperature sensor or temp average sensor or filtered temp sensor.  This should be located physically within the breeze area of the fan for maximum desired affect.

Once you have the entities created or decided upon you can build the Automation.  To build the automation:  
> 1. Click on 'Create Automation
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities and values for the listed purposes.  If you have questions trial and error or hit me up on Discord.
> 4.  Test that your fan works by changing the input number and the input boolean

### FAQ for blueprint
Questions:
>  1. You can use either Metric or Imperial, but the sensor and the input_number have to be using the same scale.
>  2. The Hysteresis offset can be '0' for the simplest operation.  If you hare using the input_number to control both this and a climate integration, you may want an offset so the fan does not quick cycle.  It basically move the input_number set point by the amount you pick
>  3. You can have multiple automations running off of this with the same or different temp settings or times, but I suggest the times on 'ENABLED' versions do not overlap, or it will get very confused.

### HOW the Blueprint / Automation works
Walk-thru:
> 1. The header of the Blueprint contains the required info plus the URL from where it came from.
> 2. The input: section is where it gets the information it needs to fill in the blanks. This information is stored in the actual automation referencing this Blueprint when executing the task.
> 3. The Variables section has several entries. These are converting !inputs to variables that can be used in templates.
> 4. The triggers section has hooks for the listed things.  2 of them are used to stop the automation at the appropriate time, and the rest are used to start the automation or to adjust the fan speed on temperature changes.
> 5. In the action the first test looks to see if the automation wants to stop.  If that is not the case, it will test the temperature reading against the set point and adjust the fan speed accordingly.

## Changelog

* **2021-08-02**: First blueprint version :tada:
                        needs Home Assistant Core 2021.7 or higher for Trigger_ID to work
* **2021-08-04**: Remove Default path as it made my fan beep for no reason.
* **2021-08-19**: Remove negative Temp Gap hysteresis, logic wrong.
* **2021-09-03**: Add Description.
* **2021-11-20**: Add Minimum Home Assistant version.

# All My Blueprints

```https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md```


## Contact Links or see my other work:

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## If you want to support me:

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

Cash App $CASHTAG: https://cash.me/$SirGoodenough

Venmo cash link: https://venmo.com/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough