# HubitatCustom

## Current Plans . . .
Feb. 2, 2021: Update - I'm still working on revisions with focus on better endpoint support and better handling of concurrency. This will probably be a few more weeks.

### Donate
Some have asked if they could donate something to me for this work.  I am not asking for donations for myself. However, if this driver helped you, I ask instead that you take whatever you think you would have donated and find food bank or other charity in your area and donate it to them instead (there are plenty of online foodbank sites). Here's one I can suggest: https://foodbankcenc.org/ . I opened an issue "Donate"- let's hear from those who have given something in response!

### What's New - Beta Version 0.0.8
Version 0.0.8
Fixes for lock reporting and meter reporting. Meter reporting (and central scene reporting) will be further revised after Hubitat 2.2.5 (currently, a bug exist in parsing meter and central scene reports which I understand will be fixed in the 2.2.5 release).

Version 0.0.7
- Additional fixes for parameter settings were added.

Version 0.0.7 adds rudimentary support for devices with multiple endpoints.  The following devices should work . . .
* Zooz ZEN 16
* Zooz ZEN 20 
* Zooz ZEN 25 -- But avoid this device until there is a fix for firmware bug. See: https://community.hubitat.com/t/incident-zooz-double-plug-model-zen25/58017
* Zooz ZEN 30
* Inovelli LZW36 (partial - still working on the setSpeed controls

To use a device with multiple endpoints:
1. Install the driver on the Parent device
2. Click on the Delete Child Devices control to get rid of child devices created by any old drivers
3. Click on the Create Child Devices control. 
4. Then reboot.


Scroll to the end of this README to see a list of known issues and version history info!

# Advanced Zwave Plus Dimmer driver  and Switch driver- Beta Releases!

The file "Advanced Zwave Plus Dimmer Driver.groovy" is a dimmer driver file, and Advanced Zwave Plus Switch Driver.groovy" a Switch driver that can identify all the parameters for a device and provides input controls allowing the setting of each parameter.

Central-Scene and Metering are both supported.

The way this works is that the driver queries the opensmarthouse.com database using the device's manufacturer, device type, and device ID information to retrieve a database record identifying all the parameters for the device. That information is then saved in the device's "state".

#### This is still a work-in-progress. 

Some tips:
* Install the driver on the "Driver Code" page. It will appear with the name "Advanced Zwave Plus Dimmer
* Go to the device that you want to work on and select this driver as the device's driver "Type".
* Click on the "Reset Driver State Data" button to clear the stored "state" inforamtion from the prior driver.
* Click on the "Initialize" control to pull the data from the database and to poll your device for its current parameter settings.
* After this completes, then click on "Save Preferences" and the web page ill now refresh. After it refreshes, the "Preferences" area should now show controls for all of the parameters.  If everything worked right, the controls should show the current settings of your device
* You should now be able to change / udpate the parameters.

* Its recommended that you reboot after assigning the driver to your devices.

# Known Problems
* For some devices, a "physical" event will follow a digital event. I believe this is due to fact that some devices automatically report their status whenever they are changed (thus, generating a second event), while other devices require the developer to generate the event.  This doesn't seem to cause any errors, so its in the "live with it for now" category while I fix other stuff.
* Bitmap inputs are poorly supported.

# Version History
0.0.7 - Numerous fixes for setting of parameters. Range checking on parameter inputs. Fixed errors in handling meter reports from devices with multiple endpoints. Additional support for multi-endpoint devices.
0.0.6 - Numerous fixes for setting of parameters. Fix to avoid trying to set a "null" parameter. If currently stored paramenter is a "null" then try to re-get parameters on an Update.


