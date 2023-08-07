# Update NewRev from 2022-03-01-A

Home Assistant changed the naming convention of Discovery MQTT entries in the back end. In order to facilitate that change, a new entity for the side number storage is required.

For this change to complete, you will need to remove the old one manually as it is no longer needed. If you do not remove the old one, it should continue to work until the deprecation ends and then is likely to cause problems. You will need to complete this action at some point.

First navigate to Devices and find the number helper created by this blueprint. It should look like the cube friendly_name followed by:
    ```_Number_Helper```

![Find the Device to remove](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/Z2MHelperDevice.png?raw=true "Find the Device to remove")

Click on the row.

Find the shish-ka-bob expanded menu icon next to "VISIT" and click that.

![Delete the Device](https://github.com/SirGoodenough/HA_Blueprints/blob/master/images/UpdasteDeleteMe.png?raw=true "Delete the Device")

Click the red "Delete"

This will remove the old Device from the MQTT stack.

The next time you activate the cube a new Device will be generated with the new name. Don't fret if the new Device is already there before you delete the old one, it will just start working now that the old one is gone.