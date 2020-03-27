## IMPORTANT NOTE!

**Before you proceed, this guide will only work if your old Spike version is version 3.6.1 or higher.

If by any chance your old Spike is lower than version 3.6.1 and you still want to migrate all your data and settings then please follow this [guide](https://github.com/SpikeApp/Spike/wiki/Backup-Database-Using-iMazing) to backup your database and then return here for the restore steps.

## Backup Current Data & Settings

Follow the appropriate steps depending on your iOS version. If by any chance you're on iOS 11 or above and you can't find the Spike database then just follow instructions for iOS 10 or below.

### iOS 11 or above 

Open the Files app on your device home screen.

[[https://spike-app.com/wiki/images/ignition/migration/17.jpg]]

Go to the "On My iPhone" section.

[[https://spike-app.com/wiki/images/ignition/migration/18.jpg]]

Open the Spike folder. DO NOT TRY TO OPEN THE DATABASE! If you open the database and end up deleting all your data just open Spike App Center, go to Settings > Maintenance > iCloud and press "Restore". After the restore process is done you should have recovered most of your data and you can restart this guide.

[[https://spike-app.com/wiki/images/ignition/migration/19.jpg]]

Press the select button.

[[https://spike-app.com/wiki/images/ignition/migration/20.jpg]]

Select Spike's database and press the "copy" button. 

[[https://spike-app.com/wiki/images/ignition/migration/21.jpg]]

Copy Spike's database to your iCloud drive.

[[https://spike-app.com/wiki/images/ignition/migration/22.jpg]]

Go back to the main menu and head over to Locations > iCloud Drive. Make sure you can see your Spike database there. We will restore it later.

[[https://spike-app.com/wiki/images/ignition/migration/23.jpg]]

### iOS 10 or below 

Open Spike and head over to settings > maintenance and press the "Send Database" button to send a copy of your current database to your e-mail address. Do not use the iCloud option to perform the migration, it will not work!

[[https://spike-app.com/wiki/images/ignition/migration/01.jpg]]

Write your e-mail address and press "Send".

[[https://spike-app.com/wiki/images/ignition/migration/02.jpg]]

Wait until Spike shows you a success message.

[[https://spike-app.com/wiki/images/ignition/migration/03.jpg]]

Just to make sure, please open your e-mail on your phone and confirm that you've received your Spike database.

Note: If you can't open your old Spike because it has expired or is revoked, please follow this [guide](https://github.com/SpikeApp/Spike/wiki/Backup-Database-Using-iMazing) to backup your database and then return here for the restore steps

## Install Spike

Now that the database has been backed up you can install Spike by following any of the available methods [here](https://spike-app.com/#installation).

## Restore Your Data & Settings

The last thing to do is restore all your data and settings to the newly installed Spike. Please follow the appropriate steps depending on your iOS version:

### iOS 11 or above 

Make sure your new Spike is installed and completely closed from the app switcher (double press the home button or swipe from the bottom of the screen on iPhone X or above and if you see Spike on the list of apps swipe up on it to close it).

Open the Files app once again and go to Locations -> iCloud Drive. Now press the "Select" button.

[[https://spike-app.com/wiki/images/ignition/migration/24.jpg]]

Select your previously backed up Spike database and press the "Copy" button.

[[https://spike-app.com/wiki/images/ignition/migration/25.jpg]]

Copy your previously backed up Spike database into your newly installed Spike (Locations -> On My iPhone -> Spike). If by any chance iOS asks you if you want to overwrite your existing database just press "Yes".

[[https://spike-app.com/wiki/images/ignition/migration/26.jpg]]

Note: If by any chance, after you open Spike your transmitter does not automatically connect please go to Spike's main menu > transmitter, press forget and then press scan. If that doesn't work, try to turn your Bluetooth off and on. Users that don't have the scan/forget button just restart your phone and all should start working again.

### iOS 10 or below 

Open Spike, allow it to send you notifications and red and accept all the disclaimers. Afterwards minimize Spike (don't close it from the app switcher!) and open the email with your Spike database that you sent yourself earlier and tap to download the database.

[[https://spike-app.com/wiki/images/ignition/migration/13.jpg]]

After your database has been downloaded, gently tap it again until you see a popup and scroll down until you see the option "Copy to Spike". Tap on it.

[[https://spike-app.com/wiki/images/ignition/migration/14.jpg]]

Spike will open and will ask you if you want to restore the database. Select "Yes".

[[https://spike-app.com/wiki/images/ignition/migration/15.jpg]]

After the database is restored Spike will warn you that you need to restart the app. Just press the "Terminate Spike" button and then open Spike once again.

[[https://spike-app.com/wiki/images/ignition/migration/16.jpg]]

Note: If by any chance, after you open Spike your transmitter does not automatically connect please go to Spike's main menu > transmitter, press forget and then press scan. If that doesn't work, try to turn your Bluetooth off and on. Users that don't have the scan/forget button just restart your phone and all should start working again.

### Soft Reset Your Device

This step is optional but HIGHLY recommended to ensure the migration goes slowly.

After completing all the steps above do a soft-reset on your device to restart iOS.

For all iPhone models below the 7 (not included) just press and hold the power and home buttons at the same time and keep them pressed until your phone reboots and you see the Apple logo. As soon as the logo appears you can release both buttons. For iPhone 7, press and hold the power and volume down buttons at the same time and keep them pressed until your phone reboots and you see the Apple logo. As soon as the logo appears you can release both buttons. For iPhone 8/X/Xs/XsMax/Xr, briefly press and release the volume up button, then immediately press and release the volume down button, and then press and hold the power button until the phone reboots and you see the Apple logo. As soon as the logo appears you can release the power button.

### Troubleshooting Dexcom/BluCon Nightrider

If your newly installed Spike is losing connection to your Dexcom transmitter then try this:

1) Go to iOS settings -> Bluetooth press the (i) icon next to your Dexcom transmitter and press forget.

2) Soft reset your phone. For all iPhone models below the 7 (not included) just press and hold the power and home buttons at the same time and keep them pressed until your phone reboots and you see the Apple logo. As soon as the logo appears you can release both buttons. For iPhone 7, press and hold the power and volume down buttons at the same time and keep them pressed until your phone reboots and you see the Apple logo. As soon as the logo appears you can release both buttons. For iPhone 8/X/Xs/XsMax/Xr, briefly press and release the volume up button, then immediately press and release the volume down button, and then press and hold the power button until the phone reboots and you see the Apple logo. As soon as the logo appears you can release the power button.

3) Open Spike, go to the "three dots" menu and press "No Lock".

4) Keep Spike open without locking your device or navigating to another app. Leave Spike in the foreground.

5) A few minutes afterwards you'll get a new pairing request. Accept it (be fast, it only appears for a few seconds)

The Bluetooth connection should improve afterwards...

### Troubleshooting MiaoMiao/Others

If your newly installed Spike is losing connection to your transmitter then try this:

1) Go to Spike Main Menu > Transmitter and press "Forget".

2) Go to iOS Settings > General > Reset and press Reset Network Settings. Phone will reboot.

3) Go to Spike Main Menu > Transmitter and press "Scan".

Disclaimer: When resetting the network settings you will need to enter all your wifi passwords again.