This is a SCRIPT Blueprint that uses my Broadlink RM3 to turn my TV on and get it into the correct mode, IE: antenna, FireTV, Chromecast, etc.  The defaults are specific to me and you should change them to match your situation. 

## :arrow_down: Get Started

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2FBroadlink_ON_script.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml

## :page_facing_up: Description 

This is a Script Blueprint that takes on the huge mess of scripts created by the Standars Broaslink Integration.  If you have a Boradlink that helps run your TV, yu know exactly what I mean.  Wvwey buyyon and function and button sequence on your remot becomes another script that must be called to get stuff done.  It's hard enough to remember what button on the remote itself, remembering all the names of the buttons it impoeeible.

The script template built with yjis giveds you a common scenario for turning your stuff on and putting the device in the correct mode to do the thing yu want to do.  I have a number of this blueprint script created in my system and here is a shot of them:

![My Buttons in Lovelace](images/Screenshot_2022-01-08_20-11-15.png)

You can import the script blueprint via the button above or manually as below.
To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
>  ◦   ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/Broadlink_ON_script.yaml```

This is my version and has defaults specific to my system that will need to be changed for your system,  Also if an !input has a default, the calling script is not required to include input data for that !input, but if you want to change the input values without editing the blueprint defaults, then add more selectors to overwrite with your desired values.

## Changelog

* **2021-09-14**: First blueprint version :tada:
* **2021-11-20**: Changes because of release of Blueprint Script UI
* * Add Minimum Home Assistant 2021-11-0

