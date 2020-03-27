Spike supports visualization of IOB and activity curves when active insulin treatments are present (bolus and/or meal) as well as COB curves when active carbohydrate treatments are present (carbs and/or meal). Absorption curves are available for both IOB/COB algorithms (Nightscout and OpenAPS). For more info about the different algorithms supported by Spike please head over to the [IOB COB Algorithms Wiki](https://github.com/SpikeApp/Spike/wiki/IOB-COB-Algorithms).

## Insulin Absorption Curves

Spike is capable of plotting IOB and activity curves and both curves can be accessed by pressing the IOB pill on the upper right corner of the chart screen when there's active IOB. If there's no active IOB, pressing the pill have no effect.

Once the pill is pressed a popup will show displaying two curves:

* **IOB:** Represents how insulin is absorbed, over time (past present and future), by the body. This curve is also useful to determine at what exact point in the future all insulin will be fully absorbed.

* **Activity:** Represents the degree and speed at which insulin is being absorbed and activated at each exact moment in time. In essence, it shows how much impact insulin is having on the body. This curve is also useful to determine if peak insulin activity has already been reached.

[[https://spike-app.com/wiki/images/absorptioncurves/01.jpg]]
[[https://spike-app.com/wiki/images/absorptioncurves/02.jpg]]

## Carbohydrate Absorption Curve

Similar to the insulin curves, this curve can be accessed by pressing the COB pill on the upper right corner of the chart screen when there's active COB. If there's no active COB, pressing the pill will have no effect.

* **COB:** Represents how carbohydrates are absorbed, over time, by the body. When using the Nightscout algorithm, the COB curve will also predict how carbohydrates will be absorbed in the future. Spike is able to calculate these predictions because the Nightscout algorithm assumes carbohydrates are absorbed in a linear fashion which can be inaccurate/misleading. When using the OpenAPS (oref0) algorithm, the COB curve will only display past and present times. Because the OpenAPS algorithm calculates absorption of carbohydrates by constantly analyzing the user's glucose trend, it's impossible to predict the future but, on the other hand, provides MUCH better accuracy when calculating COB values. For more info please head over to the [IOB COB Algorithms Wiki](https://github.com/SpikeApp/Spike/wiki/IOB-COB-Algorithms).

[[https://spike-app.com/wiki/images/absorptioncurves/03.jpg]]
[[https://spike-app.com/wiki/images/absorptioncurves/04.jpg]]