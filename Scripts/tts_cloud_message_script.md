Script Blueprint for a Nabu-Casa tts-cloud-say message. Home Assistant 

# :arrow_down: Get Started tts_cloud_say version

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint 

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FScripts%2Ftts_cloud_message_script.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.yaml

## :page_facing_up: Description

This version uses tts_cloud_say to send the message. This is is available only if you are a subscriber to Nabu-Casa.

## :gear: Usage
### Installation
You can import the script blueprint via the button above or manually as below, however it does not show in the UI as there is no Script Blueprint UI and it is not an Automation Blueprint. 
To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GIST on GitHub:
>  ◦   ```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Scripts/tts_cloud_message_script.yaml```

### Home Assistant
Once installed, go into blueprints and use this to add a script with your variables.  Answer the required questions and you can change or ignore the ones with defaults.  Remember the name you typed in.  For this example, we will suppose you named the script: 
```TTS Test Two```
After that, where ever you want this TTS to sound off in another script or an automation, you simply add a service:  (See full examples in my configuration, link below.)

```yaml
- service: script.tts_test_two
```

This makes your automation very clean looking and you move all the 'noisy' code elsewhere.  It has greatly improved my ability to think out automations.  This also keeps me from having to write the same code over and over for every TTS I want to send out.  I have almost 30 different messages in my [Home Assistant Configuration](https://github.com/SirGoodenough/Home-Assistant-Config) 

This is a very simple sample test case, I wanted to see if it would work. To my delight I have been replacing all the TTS instances in my configuration with this blueprint. It puts all the mess in one place. To call a specific message, I just fire the calling script and I have a 1 liner, done.

## :bulb: Fun Ideas
I have recently found that the !input will accept templates. Who knew, right? I have a few TTS instances that call for a random response, I just need the sound for timing of something I'm doing, and I found that something like this craziness works. It is the lyrics from a song and when triggered, it just picks one of them to play using random. It also picks a random dialect of English to speak the message from the list. Pretty slick, right?
**NOTE:**  After this was edited to get a pick list, you will need to manually edit the blueprint to change the language to a text input field or you will need to manually edit the script calling blueprint to similar values.

![Screenshot_2021-12-15_13-40-52](https://user-images.githubusercontent.com/47349533/146256617-047a05e7-5f45-4d44-b33e-29938cbe571c.png)

## Changelog

* **2021-08-26**: First blueprint version :tada:
* **2021-11-20**: Changes because of release of Blueprint Script UI 
* * Add Minimum Home Assistant 2021-11-0
* **2021-12-24**: Add pick list of all the available languages,

# All My Blueprints

https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md