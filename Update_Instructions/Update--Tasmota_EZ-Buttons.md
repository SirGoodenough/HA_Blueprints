# Update 2023-08-07 from 2023-05-01

Home Assistant changed the naming convention of Discovery MQTT entries in the back end. In order to facilitate that change, internal name changes were required.

For this change to complete all you need to do is replace the old rev blueprint with the new rev blueprint and run ths script you originally created to use the blueprint.  This re-generates everything and it will all work as before. No entity names should be effected and all your dashboard links will work as before.

If you don't do this upgrade, there **may** be problems when the deprecation is complete and the old naming convention no longer works.
