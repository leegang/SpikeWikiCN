The 3.5.2 release of Spike brings support for Dexcom Share follower mode. Users can follow users that use the official Dexcom app or follow another Spike users through Dexcom Share.

Dexcom Share servers only support glucose data. This means that Spike users following Dexcom Share masters will only have access to glucose data. All features related to treatments will be disabled in Spike follower.

If you want to be a follower and have access to the master's treatments consider using Spike in Nightscout follower mode. To do this please follow this [tutorial](https://github.com/SpikeApp/Spike/wiki/Spike-Follower-Mode).

## Follow Official Dexcom App Users

When using Spike to follow a user that uses the official Dexcom app to connect to a CGM transmitter, Spike needs to be configured manually. Don't worry, it only takes a minute.

In Spike, go to main menu > settings > general > data collection:

1) Select follower mode.
2) Select Dexcom service.
3) Type the master's username and password.
4) Select the correct Dexcom server (Dexcom accounts created in the USA should select US, everyone else should select International).
5) Press login.

[[https://spike-app.com/wiki/images/dexcomfollower/01.jpg]]

All set, if you now return to the home screen you should see the master's glucose data.

## Follow Other Spike Users

When using Spike to follow another Spike user, Dexcom Share follower mode can be configured manually as described above or using a QR Code. Using a QR Code allows the configuration process to be done automatically and the follower doesn't need to know the master's password to configure Spike.

On Spike master go to main menu > settings > share > dexcom share. Make sure your credentials are set and Spike is logged in and already sending data to Dexcom Share servers. Now press on the "Manage Users" button.

[[https://spike-app.com/wiki/images/dexcomfollower/02.jpg]]

Now choose Spike as the follower app. If your follower is planning on using the official Dexcom Follow app you should select Dexcom Follow.

[[https://spike-app.com/wiki/images/dexcomfollower/03.jpg]]

A QR Code will be generated. If you have access to the follower's device, you can scan the QR Code directly from the master's screen, otherwise you have the option to send the QR Code to the follower's email address.

[[https://spike-app.com/wiki/images/dexcomfollower/04b.jpg]]

Now, on the follower's Spike, go to main menu -> settings -> general -> data collection and press the "Scan QR Code" button. Using your device's camera scan the master's QR Code (either directly from the master's device or from the follower's email inbox in case the QR Code was sent by email).

[[https://spike-app.com/wiki/images/dexcomfollower/05.jpg]]

All set! Spike follower is now fully configured.
