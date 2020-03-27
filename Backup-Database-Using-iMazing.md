## Download iMazing

iMazing is a free app compatible with Windows and Mac. It allows the user to extract data from apps and will be used to get a backup of Spike's TestFlight database so we can later import it into Spike App Center. Please head over to https://imazing.com/download and download/install iMazing on your PC.

## Install iMazing

First install iMazing. If you're on a Mac just drag the iMazing app to your Applications folder. If you're on a PC just click the installer and follow the on-screen instructions.

[[https://spike-app.com/wiki/images/migration/iMazing01.jpg]]

## Export Spike's App Center Database

Now open iMazing and if it asks you to register just press "Later". There's no need to buy iMazing to perform Spike's database migration.

[[https://spike-app.com/wiki/images/migration/iMazing02-a.jpg]]

Connect your phone via USB to your PC, select it on the left menu and go to "Manage Apps".

[[https://spike-app.com/wiki/images/migration/iMazing03.jpg]]

Select the tab "Device" to manage apps installed on your device, in this case we will manage the old Spike App Center.

[[https://spike-app.com/wiki/images/migration/iMazing04.jpg]]

Scroll until you find Spike, right click on it and select "Backup App Data". 

[[https://spike-app.com/wiki/images/migration/iMazing05.jpg]]

Select the destination folder where you want to save Spike's App Center database (Desktop is a good candidate) and then click "Next".

[[https://spike-app.com/wiki/images/migration/iMazing06.jpg]]

Click "Ok" on the next screen.

[[https://spike-app.com/wiki/images/migration/iMazing07.jpg]]

Now let iMazing perform the backup. Depending on the amount of overall data you have on your phone and your phone's speed, this can take a while.

[[https://spike-app.com/wiki/images/migration/iMazing08.jpg]]

After the backup is finished just click "Close Window" and then close iMazing completely, we don't need it anymore. You can also uninstall it if you want. If you're on a Mac you can use the AppCleaner app to uninstall iMazing and the backup you just created so you can save some space on your hard disk drive https://freemacsoft.net/appcleaner/

[[https://spike-app.com/wiki/images/migration/iMazing09.jpg]]

Now navigate to the folder where you asked iMazing to backup Spike's data, in this case Desktop, and you will see an .imazingapp file.

[[https://spike-app.com/wiki/images/migration/iMazing10.jpg]]

Rename the .imazingapp extension to .zip

If you can't see file extensions on your PC please follow these links to learn how to enable them:

Windows: https://www.howtogeek.com/205086/beginner-how-to-make-windows-show-file-extensions/

Mac: http://www.idownloadblog.com/2014/10/29/how-to-show-or-hide-filename-extensions-in-os-x-yosemite/

[[https://spike-app.com/wiki/images/migration/iMazing11.jpg]]

Now extract the zip file and navigate to Container -> Library -> Application Support -> com.spike-app.spike -> Local Store and email the spike.db file to yourself. If you can't find the spike.db file in that directory please try Container -> Documents.

[[https://spike-app.com/wiki/images/migration/iMazing12.jpg]]

If you're migrating from Spike App Center to Spike Ignition you can now safely delete (uninstall) the Spike App Center app from your phone and continue will the Ignition guide available here: https://github.com/SpikeApp/Spike/wiki/Migration-to-Ignition-Store#install-spike-ignition-version