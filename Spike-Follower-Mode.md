Spike allows users to follow other users by using a Nightscout site that acts as a proxy. Spike in follower mode can follow users using Spike in master mode or any other app that can share data to a Nightscout site, like xDrip+ for Android.

Spike followers will have access to most of the features available to masters, like settings alarms, sharing glucose values to a watch, viewing and adding treatments, etc.

## Set Up Nightscout

In order to set Spike in follower mode the user first needs to set up a Nightscout site. The process can be a bit daunting for beginners but just follow this tutorial and you'll be running a Nightscout site in less than 20 minutes.

Setting up a Nightscout site also brings many other advantages to Spike users, like full feature reports that can be printed and taken to doctor appointments.

Note: Please follow this tutorial using a browser on a computer. Don't try to do it using your phone.

## Create an Heroku Account

Heroku is a free web based app hosting service that can be used to host your Nightscout site. 

Please visit this URL and setup a free Heroku account: https://signup.heroku.com

[[https://spike-app.com/wiki/images/follower/01.jpg]]

After you fill the form above with your info and submit it you will receive an email from Heroku asking you to confirm your account. Open the email and click the verification link.

You will now be taken to the following page. Choose a password an log in.

[[https://spike-app.com/wiki/images/follower/02.jpg]]

If you're directed to the following page it means you've successfully created your Heroku account.

[[https://spike-app.com/wiki/images/follower/03.jpg]]

The Heroku part of the tutorial is done. Now let's create a GitHub account.

## Create a GitHub Account

Head over to https://github.com and fill in the form to create a GitHub account.

[[https://spike-app.com/wiki/images/follower/04.jpg]]

On the next screen, select the following settings and click "Continue".

[[https://spike-app.com/wiki/images/follower/05.jpg]]

On the last screen, just click "skip this step".

[[https://spike-app.com/wiki/images/follower/06.jpg]]

Final step is to open your inbox, find the email GitHub just sent you, open it and click the enclosed link to verify your account. We're done here.

## Deploy Nightscout to your Heroku

Navigate to the following URL: https://github.com/nightscout/cgm-remote-monitor

On the upper right corner click the "Fork" button.

[[https://spike-app.com/wiki/images/follower/23.jpg]]


Wait a few seconds to allow Nightscout's code base to be copied to your GitHub account.

[[https://spike-app.com/wiki/images/follower/24.jpg]]

Now scroll down until you see the purple button that says "Deploy to Heroku" and click on it.

[[https://spike-app.com/wiki/images/follower/07.jpg]]

You will be presented with the following screen. Follow the tips. Don't forget to write down your API Secret in a note or a safe place, you'll need it later. 

NOTE: Your API Secret needs to be 12 characters or longer!

[[https://spike-app.com/wiki/images/follower/08b.jpg]]

Choose your unit and plugins that you want to enable. Nightscout allows you to enable a vast amount of plugins. The most relevant ones for Spike users are: "careportal basal iob cob sage boluscalc food rawbg". **Copy/paste everything inside the quotes (but don't include them) and paste it into the enable field (spaces between plugin names is required). THIS IS EXTREMELY IMPORTANT, IF YOU DON'T ADD THESE PLUGINS SPIKE WILL NOT WORK!** 

If you want to add more plugins just write them in the enable field with spaces between them. Here' a list of plugins available in Nightscout: https://github.com/nightscout/cgm-remote-monitor#plugins

[[https://spike-app.com/wiki/images/follower/12.jpg]]

Keep scrolling and follow the tips shown on the next images.

[[https://spike-app.com/wiki/images/follower/09.jpg]]
[[https://spike-app.com/wiki/images/follower/10.jpg]]

No need to set up maker keys. Just scroll all the way down and click "Deploy app".

[[https://spike-app.com/wiki/images/follower/13.jpg]]

After a minute or so Heroku will ask you for your credit cards details. Don't worry, you will not be charged. They just want your details so they can verify your identity and avoid people abusing their platform. Just fill in your details in the screen below and click "Save Details".

[[https://spike-app.com/wiki/images/follower/14.jpg]]

After a few minutes you should see a screen saying your Nightscout instance has been successfully deployed to your Heroku. If it shows an error just click "Deploy app" again, that tends to fix the issue.

[[https://spike-app.com/wiki/images/follower/15.jpg]]

Congrats. You now have Nightscout installed. But we're not done yet!

Click the button that says "View" and you will be redirected to your Nightscout site.

## Configure Nightscout

As soon as you visit your Nightscout site you'll be presented with a message telling you to configure your profile. Click "Close" and you will be taken to your profile page.

[[https://spike-app.com/wiki/images/follower/16.jpg]]

You will now need to at least configure your timezone (don't leave it as UTC, select your region). If you use treatments in Spike its a good idea to also configure your Nightscout profile with the same values you have in Spike like DIA, Carb Absorption Rate, etc...

[[https://spike-app.com/wiki/images/follower/17.jpg]]

After you're done configuring your profile scroll to the bottom and click "Authenticate" and insert your API Secret (password). Afterwards just click "Save".

[[https://spike-app.com/wiki/images/follower/18.jpg]]

We're almost done... Remove the /profile part on the URL displayed on the upper bar of your browser and press ENTER. You will be redirected to your Nightscout site. It's still empty, we will work on that next. But first, enable some plugins as described in the image below.

[[https://spike-app.com/wiki/images/follower/19a.jpg]]

We're done with Nightscout. Be sure to write down your URL and your API Secret and keep them in a safe place for future reference. We will also need them for the final steps that I will describe next.

## Configure Spike Master

Now the easy part. In Spike, go to main menu -> settings -> share and enable Nightscout. Input your Nightscout URL (remove the https:// part and also the / at the end, ex: mynightscoutsite.herokuapp.com). Input your API Secret.

[[https://spike-app.com/wiki/images/follower/20.jpg]]

Press "Login" and if all goes well you should see the following message:

[[https://spike-app.com/wiki/images/follower/21.jpg]]

There's also a few optional settings that you might want to use:

1) Upload Battery Info: This option will make Spike upload your phone and transmitter battery info to Nightscout. You will be able to visualise your phone battery levels on your Nightscout. You will not be able to visualise your transmitter battery levels on Nightscout but your followers will.

2) Upload Battery Info: This option will make Spike upload your phone and transmitter battery info to Nightscout. You will be able to visualise your phone battery levels on your Nightscout. You will not be able to visualise your transmitter battery levels on Nightscout but your followers will.

3) Upload BG Predictions: Available since Spike version 3.5.0. Using the OpenAPS Nightscout plugin Spike is able to display glucose predictions directly on Nightscout's chart. Instructions on how to achieve this are available here: https://github.com/SpikeApp/Spike/wiki/Glucose-Predictions#nightscout-sync

4) Sync On Wi-Fi Only: If you're just using Nightscout for reports and/or to backup your data, this option will make Spike only upload data when you're on Wi-Fi. This can save battery life when you're on the run. If you're using Nightscout to sync values to followers this option should always be disabled.

If you now visit your Nightscout URL using a browser you should see your glucose values (and treatments) on Nightscout's main graph.

If you're only interested in using Nightscout to backup data and have access to reports then you're done here. No need to do anything else. If you want to configure followers then head over to the next step.

## Configure Spike Follower by QR Code

Open Spike on the master's device, go to main menu -> settings -> share -> nightscout and press the "Invite Followers" button.

[[https://spike-app.com/wiki/images/follower/25.jpg]]

Spike will ask you if you want to allow the follower to be able to add treatments to the master's phone and Nightscout site. If the answer is yes, you will also be asked if you want to share your current Spike profile (insulins, ISF, I:C, etc.). Sharing your profile will make sure your follower will use your pre-configured insulins when adding treatments and will also see the same glucose predictions as the master.

After answering all questions, a QR Code will be generated. If you have access to the follower's device, you can scan the QR Code directly from the master's screen, otherwise you have the option to send the QR Code to the follower's email address.

[[https://spike-app.com/wiki/images/follower/26.jpg]]

Now, on the follower's Spike, go to main menu -> settings -> general -> data collection and press the "Scan QR Code" button. Using your device's camera scan the master's QR Code (either directly from the master's device or from the follower's email inbox in case the QR Code was sent by email). 

[[https://spike-app.com/wiki/images/follower/27.jpg]]

All set! Spike follower is now fully configured.

## Configure Spike Follower Manually

Open Spike on the follower's device, go to main menu -> settings -> general -> data collection and select follower as mode and Nightscout as service. Input the same Nightscout URL. If you just input the URL the follower will only be able to "see" your data, he/she will not be able to interact with it. If you also input your API Secret the follower will also be able to insert treatments that will be synced to Nightscout and also to the master's device (useful for caregivers). 

[[https://spike-app.com/wiki/images/follower/22a.jpg]]

If you now return to Spike's main chart screen you should see the master's glucose values and treatments. 

You're done!



