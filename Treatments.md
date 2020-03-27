Since version 2.0.0 Spike now supports the following treatments:

* **Bolus:** Administration of insulin, either by using a pen or a pump. It normally represents a correction done when glucose levels are running high. Spike also supports extended/combo bolus. **The bolus treatment is not meant to be used with basal insulins.**
* **Carbs:** Ingestion of carbohydrates. Usually done when glucose levels are running low or the user eats a snack.
* **Meal:** Represents a meal consisting of carbohydrates and an insulin bolus. A meal treatment combines the carb and bolus treatments into one.
* **Temp Basal Start:** Represents a temporary basal adjustment above or below the current basal rate. Available only to pump users (Settings -> Treatments -> Profile -> User Type > Pump User).
* **Temp Basal End:** Used to end/finish a previous temp basal treatment. Available only to pump users (Settings -> Treatments -> Profile -> User Type > Pump User).
* **Basal:** Represents the administration of a long-acting insulin injection (Lantus, Levemir, etc.). Available only to MDI/Pen users (Settings -> Treatments -> Profile -> User Type > MDI/Pen User).
* **BG Check:** A visual representation of the current glucose level measured with a meter. Sometimes the user might want to check blood glucose levels with a meter but doesn't want to calibrate the sensor. This treatment is used to register the measurement in Spike without calibrating the sensor.
* **Note:** A brief record describing a specific event like "out for a run", "lunch with friends", etc.
* **Calibration:** Calibrations are added automatically to the Chart whenever the user calibrates the sensor.
* **Sensor Start:** Sensor Starts are added automatically to the Chart whenever the user starts a new sensor.
* **Exercise:** Represents a bout of exercise along with its duration and intensity.
* **Insulin Cartridge Change:** Useful for having a record and visual representation when changing/adding insulin to the user's pump or reusable pen. If Spike is connected to a Nightscout site, this treatment will be synced with the IAGE pill. A local IAGE pill is also available in Spike by pressing the +Info pill in case the user wants to know, at all times, how old the insulin is. Available only to pump users (Settings -> Treatments -> Profile -> User Type > Pump User).
* **Pump Site Change:** Useful for having a record and visual representation when changing pump's sites. If Spike is connected to a Nightscout site, this treatment will be synced with the CAGE pill. A local CAGE pill is also available in Spike by pressing the +Info pill in case the user wants to know, at all times, the number of days and hours since the cannula was last changed. Available only to pump users (Settings -> Treatments -> Profile -> User Type > Pump User).
* **Pump Battery Change:** Useful for having a record and visual representation when changing/charging the pump's battery. If Spike is connected to a Nightscout site, this treatment will be synced with the BAGE pill. A local BAGE pill is also available in Spike by pressing the +Info pill in case the user wants to know, at all times, the last time the pump battery was charged/changed. Available only to pump users (Settings -> Treatments -> Profile -> User Type > Pump User).

All treatments are automatically shown on Spike's chart.

## Configure Treatments

Before adding treatments to Spike the user needs to configure a few settings by heading over to Settings -> Treatments -> Profile. 

First and foremost **it's imperative that the user defines if a pump or pen is used to add insulin. This needs to be set in the User Type section (Pump User vs MDI/Pen User). When MDI/Pen user is selected (default), the Basal treatment will appear under the + menu on the chart screen. When Pump User is selected, the Basal treatment will not be available and instead the user will be presented with the following treatments: Temp Basal Start, Temp Basal End, Insulin Cartridge Change, Pump Site Change, Pump Battery Change**.

The next profile section, algorithm, defines what kind of IOB/COB algorithm will be used in Spike. For more information please read the dedicated [wiki page](https://github.com/SpikeApp/Spike/wiki/IOB-COB-Algorithms).

Spike supports multiple insulins with different DIAs (Duration of Insulin Action). To determine the DIA of a specific insulin please perform the steps described in this [guide](https://www.waltzingthedragon.ca/diabetes/managing-bg/adjusting-insulin-pump-duration-of-insulin-action-dia/). Although most manufacturers supply an average DIA for their insulins, it's a good idea to determine it yourself. Each person can react differently to the same insulin brand.

The DIA value will be used by Spike to calculate the user's IOB (Insulin On Board) after a bolus or meal treatment is added. Spike will calculate a combined IOB of all different types of insulins used by the user in his/her treatments.

Once all insulins have been set up, the user needs to configure his/her carb absorption rate so Spike can calculate COB (Carbs On Bard) after a carb or meal treatment is added. To determine the carb absorption rate please follow the steps described in this [guide](https://diyps.org/2014/05/29/determining-your-carbohydrate-absorption-rate-diyps-lessons-learned/).

If having a perfect COB value is not mandatory and the intention is to only use it as a reference, leaving the default carb absorption rate of 30g per hour will work for most users. Spike takes into account digestion time. Normally it takes about 20 minutes for medium-low glycemic carbs to enter the blood stream. After the user adds a carb or meal treatment, COB value will start decreasing after 20 minutes when using the Nightscout IOB/COB algorithm. This can also be overridden by defining custom absorption delay times for fast/medium/slow carbs and setting them up when adding a carb or meal treatment (Nightscout algorithm only).

The last section is ISF/I:C/BG Target/Trends. It's imperative that all these settings are correctly added to Spike if the users wants to use [glucose predictions](https://github.com/SpikeApp/Spike/wiki/Glucose-Predictions) and the [bolus calculator](https://github.com/SpikeApp/Spike/wiki/Bolus-Calculator) features.

Now that the profile has been configured, additional settings can be found in Settings -> Treatments.

* **Enable:** By default, treatments are enabled for all users. They can be completely disabled by turning the enable switch off.

* **Display On Chart:** Treatments can be enabled in Spike but disabled on the Chart. If this option is disabled, the user will be able to add treatments and they will also be synced to his/her Nightscout site. IOB and COB values will still by synced to the Today Widget and Apple/Pebble Watch but no treatments, IOB and COB will be displayed on the chart.

* **Display IOB:** When this option is disabled, the IOB pill will not be displayed on the chart. 

* **Display COB:** When this option is disabled, the COB pill will not be displayed on the chart.

* **Download NS Treatments:** When this option is enabled, Spike will try to sync treatments that the user adds on his/her Nightscout site. If a treatment is added in Nightscout, Spike will attempt to fetch it every time a new reading arrives from the transmitter or Spike is brought to the foreground. Treatments from Nightscout will show on the chart and will also be saved to Spike's internal database. When this option is enabled Spike will consume a bit more battery but it should not be too significant.

* **Loop/OpenAPS User:** If the user uses Loop or OpenAPS this option should be enabled (MDI/Pen users should leave it disabled). When this option is enabled, Spike will not use its internal IOB and COB algorithm, instead it will display IOB and COB fetched from Nightscout. These IOB and COB values represent the data calculated by Loop/OpenAPS and sent by these apps to Nightscout. When this option is enabled, Spike will only show current IOB and COB values, the user will not be able to see IOB or/and COB values from previous times of the day. MDI/Pen users that have this option disabled will be able to scroll on the chart and see retro IOB and COB values calculated by the internal algorithm.

* **Colors:** Colors can be customised for each treatment. These colors will be used by Spike to display treatments on the chart.

* **Load Default Colors:** Will reset all your treatment's colors to default values.

* **Read Instructions:** Will take you to this WiKi.

## Add a treatment

Treatments can be added directly in the Spike app, from a Today Widget or an Apple/Pebble Watch. 

**Loop/OpenAPS users should NOT insert treatments in Spike. Treatments should be inserted in Loop/OpenAPS and they will later be synced automatically to Spike. Inserting treatments in Spike is only for MDI/Pen users.**

#### Spike

In Spike, treatments can be added by going to the + menu on the chart screen. The user will be presented with a list of available treatments. Selecting a treatment will show a popup where different values can be inserted (insulin, carbs, notes, etc.). The user has the option to define the time when the treatment occurred (past or present).

#### Today Widget

After the Workflow Today Widget has been configured with Spike treatments (Settings -> Integration -> Workflow/Shortcuts), the user just needs to select the desired treatment, insert the corresponding values and click ok. The Today Widget will send the treatment to Spike's internal server and it will be added to the chart and synced to Nightscout, Apple/Pebble Watch, HealthKit, etc.

Unfortunately Workflow/Shortcuts doesn't have an alphanumeric keyboard (only numeric) so there's no way to add a custom note on the fly. The user can only have predefined notes on the Today Widget and Apple Watch. 

#### Apple Watch (Available on iOS 11+ and WatchOS 4+ only)

Apple Watch also uses the Workflow app to insert treatments in the exact same way it's done on the Today Widget. After installing the Workflow/Shortcuts app on the device, make sure it's also installed on the Apple Watch (this can be done inside the Watch app on the phone). The Today Widget workflows will be synced to the Apple Watch automatically. It's highly recommended to keep the Workflow/Shortcuts app on the Apple Watch dock for easy and quick access.

#### Pebble Watch

Pebble can be used to insert treatments in Spike by either using the PinIt or CarepPortal app. Please head over to Settings -> Integration -> Pebble to learn how to add these apps to your Pebble Watch. It's important to note that the CarePortal app has some treatments not supported by Spike (mainly directed to pump users). Spike will only accept supported treatments, the ones listed at the top of this WiKi.

## Edit a treatment

#### From Chart

All treatments on the chart are interactive. The user can touch on a treatment and a callout will appear with details specific to that treatment. Options to move or delete the treatment are also available.

#### From Treatments Manager

For more editing granularity it's recommended to use the Treatments Manager. The manager is available from the + menu on the chart screen, by selecting the last option "Treatments". A new screen will appear with a list of all treatments inserted in the last 24H. The user will be able to delete treatments or edit them with more granularity than the callout displayed on the chart.

## View Absorption Curves

Whenever there's active IOB or COB, the user can press on any of those pills to be presented with a graph that displays the absorption curve, the exact position the user is on that curve and the exact time the insulin or carbs will be fully absorbed by the body.

This feature is not available for users that have the "Loop/OpenAPS User" option enabled in Settings -> Treatments.

To read more about absorption curves please read the dedicated [wiki page](https://github.com/SpikeApp/Spike/wiki/IOB-COB-Absorption-Curves).  

## Syncing Treatments

#### Nightscout
Spike will automatically sync treatments to Nightscout if the user has Nightscout enabled in Settings -> Share. The syncing process is done automatically and doesn't require user interaction. Treatments can also be synced from Nightscout to Spike if the "Download NS Treatments" option is enabled in Settings -> Treatments. All treatments added, deleted, edited or moved in Spike are synced to Nightscout and all treatments added, deleted, edited or moved in Nightscout are synced to Spike.

#### Today Widget
Real time IOB and COB are synced to the Today Widget every time a new treatment is added, deleted, edited or moved. Synchronisation to the Today Widget will also happen every time a new reading arrives from the transmitter.

#### Apple Watch
Real time IOB and COB can be synced directly to the Apple Watch complication. To enable this feature, please go to Spike's Settings -> Watch. The user can enable IOB, COB or both. Due to space constrains, IOB and/or COB can't be displayed at the same time as the user's name, the user will need to choose one or the other.

IOB and COB can also be synced to compatible Apple Watch apps that are able to connect directly to Spike (see Settings -> Integration -> Internal HTTP Server for instructions).

#### Pebble Watch
IOB and COB can be synced directly to a Pebble Watch when using compatible watch faces like CGM Skyline. To configure Pebble watch faces to connect directly to Spike please read instructions in Settings -> Integration -> Internal HTTP Server.

#### Garmin Watch
Compatible Garmin watch apps will also display real time IOB and COB. To configure your Garmin watch to connect directly to Spike please read instructions in Settings -> Integration -> Internal HTTP Server. A list of compatible Garmin watch apps is available [here](https://apps.garmin.com/en-US/developer/f9420c47-810f-47ac-a7dd-9fa7b8ecd22d/apps).

#### Health Kit
Spike can add insulin, carbs and glucose directly to HealthKit. This option can be enabled in Spike's Settings -> Share -> HealthKit. The user can also manage what type of treatments are synced to HealthKit by opening the Health app and selecting Spike from the Sources tab.

**Loop users MUST disable HealthKit for Spike** otherwise they will have duplicate entries in HealthKit and it will make Loop deliver more insulin than needed. HealthKit can be disabled in Spike by going to Settings -> Share -> HealthKit or by opening the Health app, navigating to Sources and disabling all options for Spike (glucose can be left on).

#### IFTTT
Adding, deleting or editing treatments can also trigger IFTTT applets. The same is true for changes in IOB and COB. To learn how to configure Spike to use IFTTT please read the WiKi available [here](https://github.com/SpikeApp/Spike/wiki/IFTTT).

## Followers
Followers can see all master's treatments, either by following through a Nightscout site or Spike to Spike mode if both phones are connected to the same WiFi network.

The master's IOB and COB will also be displayed on the follower's phone. 

All sync options like having real time IOB and COB on the Today Widget, Apple/Pebble Watch, etc. are available to followers as well. 

## Basals
Basals are rendered and added differently on the chart and deserve their own section in this wiki.

#### Pen/MDI Users

Pen/MDI users need to select the appropriate mode in Settings -> Treatments -> Profile -> User Type. 

Afterwards the user needs to add a long-acting (a.k.a. basal) insulin in Settings -> Treatments -> Profile -> Insulins. When adding the basal insulin, it's imperative that the user defines the insulin type as "Long-acting" otherwise it will not be possible to add a basal treatment to Spike. It's also important that the insulin DIA is correctly set because Spike will use it to render the duration of the basal injection. If the user injects basal insulin once a day (ex: Lantus) then a DIA of 24h is appropriate, if the user injects twice a day (ex: Levemir) then DIA should be 12h, etc.

A basal treatment can be added by going to the + menu on the chart screen and selecting "Basal". A popup will appear where the user can define the amount of basal insulin, in units, to add to Spike. A basal treatment can also be added directly in Nightscout (as a Temp Basal Start treatment and Spike will then convert it to a MDI/Pen basal treatment), or using the Workflow/Shortcuts Today Widget or Apple Watch app (to add the corresponding workflow please head over to Spike Settings -> Integration -> Workflow/Shortcuts).

Once a basal treatment is added to Spike it will appear at the bottom of the chart. The length of the quad that represents the basal treatment is defined by the insulin DIA. The basal quad will also display the name of the insulin that was used for the treatment, as well as the amount and the rate of insulin units per hour.

[[https://spike-app.com/wiki/images/basals/01.jpg]]

Pressing the basal quad will make Spike display a callout with additional information. It's also possible to move or delete the basal treatment directly from the callout.

[[https://spike-app.com/wiki/images/basals/02.jpg]]

More options to edit a basal treatment are available by going to the + menu and selecting the last menu item, "Treatments".

#### Pump Users

Pump users need to select the appropriate mode in Settings -> Treatments -> Profile -> User Type. 

Afterwards, they will need to add their basal rates to Spike by going to Settings -> Treatments -> Profile -> Basals (bottom of the screen). These are the same basal rates configured in the user's pump. The user is also presented with an option called "Import from Nightscout" that will import all basal rates configured in Nightscout and will automatically add them to Spike in case the user already has his/her basal rates added to Spike and doesn't want to retype them in Spike.

Pump users can then also add temp basal treatments in Spike by going to the + menu on the menu chart and selecting the Temp Basal Start treatment. A popup will appear where the user can select the amount of insulin, if the amount is absolute (units) or relative (percentage of the current basal rate) and finally the duration of the temp basal treatment. If by any chance the user wants to cancel a previous temp basal treatment, a new temp basal end treatment can be added to Spike.

Spike can also sync temp basal treatments to and from Nightscout. Syncing temp basal treatments from Nightscout is very useful for APS users (make sure the "Download NS Treatments" option is enabled in Settings -> Treatments).

Just like for Pen/MDI users, Pump Basals are rendered at the bottom of Spike's main chart. Because of the nature of how pumps work, basals for pump users are rendered in a more complex way:

1) The dotted line represents the scheduled basal rate that has been configured in Settings -> Treatments -> Profile -> Basal Rates. Have in mind that the dotted line does not represent the real amount of basal that it's being injected into the body since a Temp Basal Treatment can override a scheduled basal rate.

2) The small quads represent Temp Basal treatments. All Temp Basal treatments are "clickable" and will display additional information and options to the user.

3) The solid line represents the actual basal amount that is being (or has been) delivered to the body. This line can be identical to the dotted line if no Temp Basal treatment is active, which means the scheduled basal rate is the actual amount that is being delivered to the body, or it can be completely different from the scheduled basal rate if a Temp Basal Start or Temp Basal End treatment is active. 

[[https://spike-app.com/wiki/images/basals/03.jpg]]

[[https://spike-app.com/wiki/images/basals/04.jpg]]

[[https://spike-app.com/wiki/images/basals/05.jpg]]

#### Common Settings

* **Display Basals on Chart:** As the name suggests, this setting will enable/disable the rendering of basals in Spike's main chart. Available in Settings -> Treatments.
* **Download NS Basals:** This option will enable/disable downloading basals from Nightscout. For Pen/MDI or Pump users, only enable this option if you plan to add basal treatments directly in Nightscout. APS users (Loop/OpenAPS) should have this option always enabled so Spike can fetch all basal treatments added by their APS. Available in Settings -> Treatments.
* **Basal Colors:** Colors for basals on the main chart can be customized by going to Settings -> Chart -> Colors or by press and holding for one second on the lower chart stats.
* **Basal Size:** Size of the basal are on Spike's main chart can be customized by going to Settings -> Chart -> Size. The size is defined as a percentage of the total chart height.