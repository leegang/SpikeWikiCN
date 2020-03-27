Since version 3.0.0 Spike now comes bundled with a bolus calculator to assist you in your insulin/carbohydrate dosages. It can be used to determine the amount of insulin needed to cover a meal, to correct a high or the amount of carbs to correct a low.

The bolus calculator can be accessed by pressing the + icon at the top of the main chart. 

## Configure Profile

Before you can use the calculator you'll need to add some settings in Spike.

Let's start by configuring your profile. Please head over to Spike settings -> treatments -> profile.

The first thing you need to configure is your insulin(s). Press the "Add" button and add your insulin(s).  You will be presented with some on-screen instructions, be sure to read them carefully.

[[https://spike-app.com/wiki/images/boluscalculator/01.jpg]]

Spike allows you to use three different kind of carbohydrates depending on their glycemic index:

* **Fast:** Fast absorption carbohydrates like glucose tabs, candy, etc.
* **Medium:** Medium absorption carbohydrates like fruit, etc.
* **Slow:** Slow absorption carbohydrates like sweep potatoes, whole grains, etc.
* **Default:** The default carbohydrate type (fast, medium or slow) that will be used in all your treatments. You will still have the option to change the carbohydrate type for each treatment you add to Spike.

You can change the default absorption times (the time it takes for the carbohydrate to start reaching your blood stream) by scrolling in the profile screen. Be sure to read the on-screen instructions.

[[https://spike-app.com/wiki/images/boluscalculator/02.jpg]]

The last part you need to configure is your ISF, I:C, BG Target and Trend Correction. Explanations for these terms are presented directly in Spike, be sure to read them. Spike also supports multiple profiles in case these settings change at different times of the day. For example, you might be more insulin resistant in the morning and more insulin sensitive at night. You can create as many profiles for different times of the day as you want, as long as the different profiles don't overlap. To set up your ISF, I:C, BG Target and Trend Correction just scroll down on the profile screen and press the "Add" button. Be sure to read the in depth explanation of each of these terms first. Spike also provides you with guides on how to determine your ISF and I:C at the bottom of the screen. Be sure to press the "Save" button after you create each of your profile.

**It's extremely important that the ISF, I:C and Trend Correction values that you add to Spike are accurate otherwise the calculator will not give you accurate results.**

[[https://spike-app.com/wiki/images/boluscalculator/03.jpg]]

## Configure Bolus Calculator

The default bolus calculator settings should be appropriate for most users but they can still be customized.

Head over to Spike settings -> treatments -> bolus calculator to change them.

[[https://spike-app.com/wiki/images/boluscalculator/04.jpg]]

* **Insulin Precision:** Determines how precise you want the calculator to be in regards to insulin recommendations. The bolus calculator supports decimal, half and whole units (0.1, 0.5, 1). 
* **Medium:** Determines how precise you want the calculator to be in regards to carbohydrate recommendations. The bolus calculator supports half and whole grams (0.5, 1). 
* **Allowed Upper/Lower BG Target Margin:** The upper/lower margin (mg/dL or mmol/L) that you find acceptable for the calculations. For example, if you set a margin of 0mg/dL and a BG Target of 100mg/dL the calculator will always give you recommendations to achieve 100mg/dL. If you set a margin of 10mg/dL and you open the calculator when your glucose is at 93mg/dL the calculator will tell you that you're still within range and no corrections need to be made, unless of corse you start adding carbs to the calculator, in that case it will present you with insulin recommendations to achieve your 100mg/dL target.
* **Auto Account For IOB:** If this option is checked, every time you open the calculator and you already have active IOB the calculator will take it into account for the calculations. Even if this option option is unchecked you can always ask the calculator to use your current IOB every time you open it by pressing the IOB check mark. If this option is activated the IOB checkmark will be checked by default. 
* **Auto Account For COB:** If this option is checked, every time you open the calculator and you already have active COB the calculator will take it into account for the calculations. Even if this option option is unchecked you can always ask the calculator to use your current COB every time you open it by pressing the COB check mark. If this option is activated the IOB checkmark will be checked by default. 
* **Auto Account For Trend:** If this option is checked, every time you open the calculator and you your glucose is on an upwards or downwards trend the calculator will take it into account for the calculations. Even if this option option is unchecked you can always ask the calculator to correct your trend every time you open it by pressing the Trend check mark. If this option is activated the Trend checkmark will be checked by default. 

**Note: If you set a small precision for insulin/carbs or you have a high ISF/i:C, the bolus calculator may not fully reach your desired BG Target. In those cases, the calculator will try to get as close to your target as mathematically possible.**

## How To Use The Bolus Calculator

To access the bolus calculator just press the + button at the top of the main glucose chart in Spike and select "Bolus Calculator". You will then be presented with a popup where you can configure your desired settings.

Lets go through all available settings in the bolus calculator.

* **Blood Glucose (1):** By default the bolus calculator will display the most recent glucose value received from your transmitter and will take it into account when performing calculations. If your glucose level changes while you're in the calculator, the new value will be automatically loaded into it. If you don't want calculations to take into account your blood glucose you can turn this option of by unchecking it, this might be useful in case you want Spike to calculate the amount of insulin needed to cover a meal without taking your current glucose level into account. Spike will also allow you to set a different glucose value than the one on received from your transmitter by pressing the +/- sign next to the numeric stepper (2).  
* **Carbs (3):** If you're going to be eating some carbohydrates be sure to leave this option enabled and input the amount in grams in the numeric stepper found on the right side (4). Even if you don't plan on eating carbohydrates as long as the carbohydrate count is set to zero they will not be taken into account in the calculations. For this reason the carbs option is always enabled by default. As part of the carbs settings you will find a button named "Load Foods" (5) that will give you access the Food Manager. All foods added through the Food Manager will be automatically imported into de Bolus Calculator. For instructions on how to use the Food Manager please read the following tutorial: https://github.com/SpikeApp/Spike/wiki/Food-Manager. You can also define a carb offset (6), in minutes, in case you want to eat your carbohydrates after you bolus or if you've already eaten your carbohydrates before. The final option is carb type (7) where you're supposed to select the type of carbohydrate(s) you're going to ingest (fast, medium, slow). The carbohydrate type will directly affect the COB (Carbs-On-Board) algorithm in Spike. The faster the carb, the faster your COB will reach zero.
* **Insulin Type (8):** This option defines the insulin type that is going to be added to the final treatment. The insulins listed here are the ones you created in your profile settings. If the final treatment determined by the calculator does not need any insulin, the insulin type option will be ignored.

[[https://spike-app.com/wiki/images/boluscalculator/05.jpg]]

* **Trend (9):** The calculator can take into account your current glucose trend. Your trend is loaded into the calculator automatically every time you open it or every time the trend changes. When enabled, Spike will take the necessary correction (insulin if the trend is going up or carbohydrate if the trend is going down) into account in the final calculations. The correction amount is defined in your profile settings and the calculator will display it on the right side. In the example above the trend is flat which means no correction is necessary.
* **IOB (10):** Same as with the trend the calculator will automatically load your current IOB and will update it every time Spike receives a glucose reading from the transmitter (5 minutes intervals). When enabled (recommended), the calculator will take your current IOB in the final calculations.
* **COB (11):** Same with IOB, when this option is enabled (recommended) Spike will take into account your current COB in the final calculations.

[[https://spike-app.com/wiki/images/boluscalculator/06.jpg]] 

* **Exercise Adjustment (12):** The calculator can also take into account if you're about to do or just finished doing an exercise bout. While/after doing exercise your body will be more insulin sensitive and if you want the calculator to take this into account be sure to enable this option. If you want the calculator to give you a suggestion on how much insulin percentage should be reduced in the final treatment calculations you can define if you're about to do or just finished doing exercise (13), the intensity of the exercise (low, moderate and high) (14) and the duration of your exercise bout (15). The calculator will then give you a suggestion (16) which accounts for the amount of insulin reduction (%) that will be applied to the calculations. Have in mind that this value is just a suggestion given by the calculator, by any means it's not set in stone and you can always change the suggestion to a value that you think better reflects your needs by pressing the -/+ buttons in the numeric stepper on the right side (17). If you do change the reduction amount suggested by the calculator, Spike will remember this value every time you select the same exercise time, intensity and duration, meaning the calculator will learn from your input so you don't need to change it every time you want to apply an exercise reduction in subsequent treatments.

[[https://spike-app.com/wiki/images/boluscalculator/07.jpg]] 

* **Sickness Adjustment (18):** In times of sickness the body normally tends to become more insulin resistant, meaning more insulin will be needed to correct a high or cover carbs from a meal. If you enable this option the calculator will take this resistance into account by increasing your insulin needs in percentage points (19). You can define the amount (%) that should be taken into account in the final calculations by pressing the -/+ buttons in the numeric stepper on the right side of the screen (19).

[[https://spike-app.com/wiki/images/boluscalculator/08.jpg]] 

* **Extra Correction (21):** For the more advanced users the calculator allows you to add an extra insulin correction to the final treatment suggestion. You can set this correction by pressing the -/+ buttons in the numeric stepper on the right side of the screen (22). A positive number will increase the amount of insulin suggested in the final calculations, a negative number will increase the amount of carbs. The majority of users will not need to use with this option.

[[https://spike-app.com/wiki/images/boluscalculator/09.jpg]] 

* **Extended Bolus Reminder (23):** If you're going to consume a high fat meal (or for any other reason) you might want to do an extended bolus some time afterwards. The calculator allows you to schedule a notification for the future. To do so, just enable the reminder option (13), select a time and date when you want to be notified (24) as well as the sound for that specific notification (25). Have in mind that if you have your phone on silent (mute) you will not hear the notification sound. The same might also be true if you have your phone on Do Not Disturb (DND) mode. 
* **Note (26):** Finally, you can also set a note for your treatment that will be displayed when you press the treatment on the main chart and will also be uploaded to Nightscout.

[[https://spike-app.com/wiki/images/boluscalculator/10.jpg]] 

* **Suggestions (27):** The last part of the bolus calculator will show you the suggested calculations for your treatment. The calculator will tell you the glucose outcome without applying any treatment, the glucose outcome after applying the treatments and also the amount of insulin/carbs needed to cover your treatment. The amount of suggested insulin can be tweaked by pressing the -/+ buttons in the left numeric stepper (28) and carbs by pressing the -/+ buttons in the right numeric stepper (29). Have in mind that if you change the suggested amount of insulin or carbs the bolus calculator will switch to manual mode meaning it will still show you the outcome for your tweaked amounts but it will not automatically update your glucose level, IOB, COB and trend when a new reading arrives from your transmitter. When in manual mode, the calculator will display a message to notify you of the restrictions.
* **Add Treatment (30):** After you're comfortable with the suggestion given by the calculator you can press the ADD button to insert a treatment in Spike. If the suggested treatment contains insulin and carbs, it will be added as a meal. If it only contains insulin it will be added as a bolus and finally, if it only contains carbs it will be added as a carb.
* **Cancel (31):** By pressing the CANCEL button no treatment will be added, the bolus calculator will close and the main chart will be shown.
* **Instructions (32):** Pressing the INSTRUCTIONS button will open Safari and will take you to this WiKi.

[[https://spike-app.com/wiki/images/boluscalculator/11.jpg]] 

## Displaying Your BG Target On The Chart

Since the introduction of the bolus calculator users that set a BG target on their profile settings will now see an additional line on the main chart. If the user has multiple profiles the line will display the BG Target for the current active profile. The line can be enabled/disabled in settings -> chart and there's also an additional option to change the color. 