# Update NewRev from 2022-03-01-A

Home Assistant changed the naming convention of Discovery MQTT entries in the back end. In order to facilitate that change, a new Device is required.

For this change to complete, you will need to remove the old one manually as it is no longer needed. If you do not remove the old one, it should continue to work until the deprecation ends and then is likely to cause problems. You will need to complete this action at some point.

First navigate to Devices and find the one created by this blueprint. It should look like the printer name followed by:
    ```Blueprint Helper```

![Find the Device to remove](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/OctoprintHelperDevice.png?raw=true "Find the Device to remove")

Click on the row.

Find the shish-ka-bob expanded menu icon next to "VISIT" and click that.

![Delete the Device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/UpdasteDeleteMe.png?raw=true "Delete the Device")

Click the red "Delete"

This will remove the old Device from the MQTT stack.

The next time you start Octoprint it will create a new Device with all the same entities that existed before. If the printer is already running, you will need to restart Octoprint to enable the new Device.
