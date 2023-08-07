# Update version from 2022-03-01-A to new

Home Assistant change the naming convention of Discovery MQTT entries in the back end.  In order to facilitate that change, a new entity for the side number storage is required.

For this change to complete, you will need to remove the old one manually as it is no longer needed.  If you do not remove the old one, it should continue to work until the deprecation ends and then is likely to cause problems. You will need to complete this action at some point.

First navigaste to devices and find the number helper created by this blueprint.  It should look like the cube friendly_name followed by:
```_Number_Helper```
