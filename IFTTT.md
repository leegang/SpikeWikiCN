The 1.1.4 release of Spike brings IFTTT integration. IFTTT is an extensible system by which users can create custom recipes following an “if this then that” logic. Spike users can use IFTTT in response to “events” (like a high or low alarm, when a new glucose reading arrives from the transmitter, and alarm is snoozed, etc.). 

The potential of the IFTTT system is exciting, and users can create their own recipes using any available IFTTT channel in combination with the Maker channel. Possible applications of IFTTT integration range from sending an SMS message or making a phone call when a Spike event happens, to tweeting a Spike event, to changing the color of household lights based on a Spike event (if you use a smart lighting system like Philips hue), to notifying caregivers if your glucose gets too low or too high, etc. The possibilities are almost endless and is up to the user's imagination to create IFTTT recipes that suit his/her needs.

## Create an IFTTT account

* To get started using IFTTT and Spike, you need to first create an account on the [IFTTT site](https://ifttt.com/join). (The account is free.)

* After you have an account, you need to find your Maker key. This is shown on the [Maker Channel](https://ifttt.com/maker_webhooks) page when you are logged in. If this is the first time you use the Maker Channel, you will need to click the "Connect" button then click the "Settings" button on the top right corner and copy your unique key.

[[https://spike-app.com/wiki/images/integration/IFTTT/01.jpg]]
[[https://spike-app.com/wiki/images/integration/IFTTT/02.jpg]]
[[https://spike-app.com/wiki/images/integration/IFTTT/03.jpg]]

* After you get your Maker key you will need to insert it in Spike by navigating to settings -> integration -> IFTTT. Have in mind that Spike can trigger events in several IFTTT accounts at a time. This can be useful if you want to trigger events on caregivers accounts. If you want Spike to trigger several IFTTT accounts at the same time, just insert as many Maker keys as you wish separated by commas (,). Don't forget to also enable IFTTT at the top screen.

[[https://spike-app.com/wiki/images/integration/IFTTT/04.jpg]]

## Create an IFTTT Recipe
After you have added your Maker key(s) to Spike, you can create a recipe. As noted above, each user may find different ways to take advantage of IFTTT integration. To understand the process of creating a recipe, we will demonstrate setting IFTTT up to send a notification to your cellphone (iOS in this example) to demonstrate the process.

* Log in to IFTTT.
* Choose to “Create a Recipe” by going to [My Recipes / Create a Recipe](https://ifttt.com/myrecipes/personal/new).
* First you have to identify the THIS part of the “if this, then that” statement. Click the large blue THIS to start the process.

[[https://spike-app.com/wiki/images/integration/IFTTT/05.jpg]]

* Type “Webhooks” into the “Choose a service” search box.

[[https://spike-app.com/wiki/images/integration/IFTTT/06.jpg]]

* Click the “Webhooks” icon.
* Click the trigger (the box) shown. (In this example, “Receive a web request” is the trigger.

[[https://spike-app.com/wiki/images/integration/IFTTT/07.jpg]]

* Enter the name of the “event” you are using from available Spike events and click the "Create trigger" button. (You can review all of the possible Spike events below. For this example, enter spike-bgreading - this event will send an alert for every new readings that comes from the transmitter.

[[https://spike-app.com/wiki/images/integration/IFTTT/08.jpg]]

* Click the "Create trigger" button.
* Now click the large blue "that" to set up the second half of the recipe.

[[https://spike-app.com/wiki/images/integration/IFTTT/09.jpg]]

You can now choose from any available action channel. (Note: You may have to do additional steps to set up or configure a channel for use, including installing the IFTTT app on your cellphone and activating it.) For this example, enter “notifications” in the search box and click the "Notifications" box.

[[https://spike-app.com/wiki/images/integration/IFTTT/10.jpg]]

* If you have not connected the channel before, you may need to take steps to “connect” the selected channel. You will need to follow any necessary steps to connect the channel before you can complete the recipe. (Connecting the notifications channel will include downloading the IFTTT app, if you have not already done so.)

* Click the action (the box) shown. (In this example, the action is “Send a rich notification.”)

[[https://spike-app.com/wiki/images/integration/IFTTT/11.jpg]]

* The default notification text will be shown.

[[https://spike-app.com/wiki/images/integration/IFTTT/12.jpg]]

* You can add additional information to the notification by customising the title and clicking the “Add ingredient” icon to the right. Any or all of the available ingredients can be added to the notification text (one by one). 

[[https://spike-app.com/wiki/images/integration/IFTTT/13.jpg]]

* The following image shows a notification that will contain all available pieces of information.

[[https://spike-app.com/wiki/images/integration/IFTTT/14.jpg]]

* Click the “Create action” button.
* Give your recipe a name. (It can be anything you wish to help you know what your recipe is.)

[[https://spike-app.com/wiki/images/integration/IFTTT/15.jpg]]

* Click “Finish”
* The recipe then appears in your “My Recipes” area. You can edit it from this location at any point.
* When your recipe runs, you will receive a notification on your device. (In your device settings for notifications, you may be able to control where/how your notifications appear.)
* Using the same steps above, you can configure an SMS message to be sent when a Spike event occurs or any other event (channel) available in IFTTT.
* The final step is to go into Spike's settings and enable the "All Glucose Readings" trigger in IFTTT settings. This will make Spike trigger the spike-bgreading event on the IFTTT account.

[[https://spike-app.com/wiki/images/integration/IFTTT/16.jpg]]

## Fine-tuning Your IFTTT Recipes
The following “events” are available for Spike/IFTTT. You can create recipes specifically for any of these events. Just be aware that some of the event categories overlap. (If you receive multiple notifications when something happens, you likely need to look closely at what events you have chosen.)

* **Glucose Thresholds:** Enabling this option in Spike's settings will trigger the spike-highbgreading and spike-lowbgreading event every time you receive a reading from your transmitter that is higher or lower than the threshold you've defined.
    * Value 1: Glucose value.
    * Value 2: Slope arrow.
    * Value 3: Delta.

* **All Glucose Readings:** Enabling this option in Spike's settings will trigger the spike-bgreading event every time you receive a new reading from your transmitter.
    * Value 1: Glucose value.
    * Value 2: Slope arrow.
    * Value 3: Delta.

* **Separate IFTTT Events For Each Glucose Threshold:** Enabling this option in Spike's settings will trigger the spike-bgreading-urgent-high, spike-bgreading-high, spike-bgreading-in-range, spike-bgreading-low and spike-bgreading-urgent-low events every time you receive a new reading from your transmitter and according to the threshold (urgent high, high, in range, low, urgent low) the reading belongs to. This option is only available after enabling "All Glucose Readings". It can be used, among other things, to change the color of smart bulbs depending on your glucose level. 
    * Value 1: Glucose value.
    * Value 2: Slope arrow.
    * Value 3: Delta.

* **Internal HTTP Server Errors:** Enabling this option in Spike's settings will trigger the spike-server-error event every time the internal HTTP server goes offline.
    * Value 1: Title of the alert.
    * Value 2: Error message.
    * Value 3: N/A.

* **Glucose Alarms:** Enabling these options in Spike's settings will trigger the corresponding glucose events: spike-fast-rising-triggered, spike-fast-rising-snoozed, spike-urgent-high-triggered, spike-urgent-high-snoozed, spike-high-triggered, spike-high-snoozed, spike-fast-drop-triggered, spike-fast-drop-snoozed, spike-low-triggered, spike-low-snoozed, spike-urgent-low-triggered, and spike-urgent-low-snoozed every time a glucose alarm fires or is snoozed.

  * **Firing:**</br>
    * Value 1: Title of the alarm.
    * Value 2: Glucose value.
    * Value 3: Slope arrow and delta.

  * **Snoozing**.
    * Value 1: Title of the alarm.
    * Value 2: Snooze time in minutes.
    * Value 3: N/A.

* **Calibration Alarm:** Enabling these options in Spike's settings will trigger the corresponding glucose events: spike-calibration-triggered and spike-calibration-snoozed every time a calibration alarm fires or is snoozed.

  * **Firing:**</br>
    * Value 1: Title of the alarm.
    * Value 2: N/A.
    * Value 3: N/A.

  * **Snoozing**.
    * Value 1: Title of the alarm.
    * Value 2: Snooze time in minutes.
    * Value 3: N/A.

* **Missed Readings Alarm:** Enabling these options in Spike's settings will trigger the corresponding missed readings events: spike-missed-readings-triggered and spike-missed-readings-snoozed every time a missed readings alarm fires or is snoozed.

  * **Firing:**</br>
    * Value 1: Title of the alarm.
    * Value 2: Number of missed readings.
    * Value 3: Time since last reading.

  * **Snoozing**.
    * Value 1: Title of the alarm.
    * Value 2: Snooze time in minutes.
    * Value 3: N/A.

* **Phone Muted Alarm:** Enabling these options in Spike's settings will trigger the corresponding phone muted events: spike-phone-muted-triggered and spike-phone-muted-snoozed every time a phone muted alarm fires or is snoozed.

  * **Firing:**</br>
    * Value 1: Title of the alarm.
    * Value 2: N/A.
    * Value 3: N/A.

  * **Snoozing**.
    * Value 1: Title of the alarm.
    * Value 2: Snooze time in minutes.
    * Value 3: N/A.

* **Transmitter Low Battery Alarm:** Enabling these options in Spike's settings will trigger the corresponding transmitter low battery events: spike-transmitter-low-battery-triggered and spike-transmitter-low-battery-snoozed every time a transmitter low battery alarm fires or is snoozed.

  * **Firing:**</br>
    * Value 1: Title of the alarm.
    * Value 2: N/A.
    * Value 3: N/A.

  * **Snoozing**.
    * Value 1: Title of the alarm.
    * Value 2: Snooze time in minutes.
    * Value 3: N/A.

* **IOB Updated:** Enabling this option in Spike's settings will trigger the spike-iob event every time your IOB is updated after adding, deleting and editing a treatment. Spike will also trigger the spike-iob event every time a new reading arrives from the transmitter.
    * Value 1: IOB value.
    * Value 2: N/A.
    * Value 3: N/A.

* **COB Updated:** Enabling this option in Spike's settings will trigger the spike-cob event every time your COB is updated after adding, deleting and editing a treatment. Spike will also trigger the spike-cob event every time a new reading arrives from the transmitter.
    * Value 1: COB value.
    * Value 2: N/A.
    * Value 3: N/A.

* **IOB & COB Updated:** When both IOB and COB options are enabled, Spike will not trigger the previous two events (spike-iob and spike-cob). Instead it will trigger the spike-iobcob event every time your IOB/COB is updated after adding, deleting and editing a treatment. Spike will also trigger the spike-iobcob event every time a new reading arrives from the transmitter.
    * Value 1: IOB value.
    * Value 2: COB value.
    * Value 3: N/A.

* **Treatments:** Enabling these options in Spike's settings will trigger the corresponding treatment's events: spike-treatment-added, spike-treatment-deleted and spike-treatment-updated every time the user adds, deletes or edits a treatment. The same events are triggered for all treatments. Spike will only trigger treatments that are enabled in Spike's Settings - Integration - IFTTT.

  * **Added:**</br>
    * Value 1: Treatment Type.
    * Value 2: Treatment Value.
    * Value 3: Treatment Time.

  * **Deleted:**</br>
    * Value 1: Treatment Type.
    * Value 2: Treatment Value.
    * Value 3: Treatment Time. 

  * **Updated:**</br>
    * Value 1: Treatment Type.
    * Value 2: Treatment Value.
    * Value 3: Treatment Time. 

## Understanding IFTTT
One important thing to understand about IFTTT is that recipes you create are specific to your IFTTT account. You can’t, for example, create a recipe to send a notification to a different caregiver’s phone. That caregiver would have to also have an IFTTT account, a maker key, and individual recipes, and that caregiver’s maker key would need to be added to Spike's IFTTT settings (comma separated).

Please be sure and test your recipes. You may notice that there might be a delay with notifications and SMS messages (or other IFTTT actions) in response to Spike events. 

## Acknowledgements

Special thanks to Nightscout. Parts of this guide are based on their guide.