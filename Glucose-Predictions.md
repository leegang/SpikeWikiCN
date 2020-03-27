# 预测血糖值的算法

从3.5.0版开始，Spike可以预测长达4小时的血糖趋势。 为了实现这一点，部分OpenAPS（oref0）算法移植已被到Spike中。 该算法已经过大量修改，可用于预测以及IOB / COB计算。

预测适用于Spike的主用户，关注者，Loop / OpenAPS用户（需要在“设置”>“处理”中启用“循环/ OpenAPS用户”选项）。

尽管oref0算法的一部分现在可以在Spike中使用，但Loop / OpenAPS用户仍然需要启用“Loop / OpenAPS用户”设置，这将使Spike直接从Nightscout获取IOB / COB和预测值。因为Spike尚未考虑基础率。 因此，如果您是Loop / OpenAPS用户，请确保在“设置”>“处理”中打开“ Loop / OpenAPS”设置，以确保Spike与APS保持同步（使用Nightscout作为代理）。

## 重要

重要的是要记住，如果Spike告诉您您在2小时内的预测BG为100mg / dL，这并**不**表示在2小时内您的BG将为100mg / dL ...这意味着**如果维持当前状态**（您的BG当前正在上升/下降多少，您有多少IOB / COB等），则您的BG **应该** 在2小时内达到100mg / dL（只要DIA ，ISF，I：C等正确填写到Spike中）。 请注意 **如果** ，这非常重要。 预测不断变化，这就是为什么每次您从发射器获得新的读数或记录新的治疗方法时，Spike都会重新计算它们的原因。

## 配置

在使用预测之前，你可以/应该做一些设置。

### 注意：必须在Spike的设置中配置ISF（胰岛素敏感性因子）和I：C（胰岛素与碳水化合物的比率）。 两者都用于确定未来血糖趋势所需的所有计算中。 如果未找到ISF或I:C，则Spike的默认ISF为50mg / dL，I:C为1U:10g，这可能会导致预测不准确。 要配置您的ISF和I:C，请转到“设置”>“治疗”>“配置文件”，然后向下滚动到屏幕底部

首次安装/升级Spike时，默认情况下禁用预测。 设置完ISF和I:C后，可以通过按葡萄糖图表屏幕右上角的预测药丸并按启用开关（启用=蓝色，禁用=灰色）来启用预测。

启用预测后，将为用户提供更多设置和其他信息。 现在，我们将仅关注设置，稍后将解决其余问题。

* **启用:** 启用预测后，将为用户提供更多设置和其他信息。 现在，我们将仅关注设置，稍后将解决其余问题。

* **持续时间:** Spike应该在多远的将来预测您的血糖值。 Spike可以预测未来最多4h，但并非所有图表视图都可以预测。 在1h模式下查看图表时，最多可以预测30分钟，3h模式最多可以预测1小时30分钟，6小时模式最多可以预测3小时，而12 / 24小时模式最多可以预测4小时。 每种图表模式的持续时间分别保存在Spike的数据库中，这意味着您可以分别设置每种图表模式的持续时间，并且这些持续时间将在应用程序/系统重新启动时持续存在。 此设置适用于主账号，关注者和Loop / OpenAPS用户。
* **包括IOB / COB：** 此设置将告诉Spike在执行确定未来血糖趋势的所需计算时是否应考虑当前的IOB / COB。 计入IOB / COB将使预测更加有效。 如果关闭此设置，Spike将仅考虑当前的葡萄糖趋势和势头来计算预测。 此设置仅适用于主账户和关注者，而不适用于Loop / OpenAPS用户。
* **单一预测曲线：** Spike最多可以同时显示4条预测曲线（IOB，COB，UAG和ZT ...我们稍后会介绍）。 启用此设置后，Spike将仅显示默认曲线，而忽略其他曲线（Spike会在任何特定时间自动尝试确定哪一条曲线最相关/最精确，并将其标记为默认曲线）。 只建议新手用户启用此设置。 建议资深用户不要开启此设置，并在Spike的图表中显示所有预测曲线，以更好地了解将来所有可能的血糖情况。 此设置适用于主账户，关注者和OpenAPS用户。 Loop用户无法使用该功能，因为Loop仅使用一条预测曲线，因此该设置无关紧要。
* **刷新预测:** 此功能仅适用于Loop / OpenAPS用户。 这是因为，对于这些特定用户，Spike将直接从Nightscout获取预测，而不是在应用内进行计算。 这样可以确保Spike中显示的预测与用户APS中显示的预测实时同步。 因为Spike直接从Nightscout获取预测，所以有时它们可能有几分钟不同步。 如果用户想强制刷新而不是等待Spike自动执行获取操作，则可以按“刷新预测”按钮，这将使Spike立即连接到Nightscout并获取最新的可用预测数据。 只有在“设置”>“服务”中启用了“Loop/ OpenAPS用户”设置的用户才能看到此功能。

[[https://spike-app.com/wiki/images/spikepredictions/02.jpg]]

## 理解预测

如前所述，Spike最多可以同时显示4条预测曲线。 如果曲线增加了与整个上下文的相关性，则仅在屏幕上可见。 例如，仅当当前有活动的COB时，才会显示COB曲线。

让我们了解每条曲线：
* **IOB (在途胰岛素):** 这是仅基于胰岛素的预测BG曲线。 如果不存在胰岛素（IOB），则此预测的BG曲线将仅考虑当前的BG趋势和诸如“ BG态势”之类的信息。 当存在胰岛素（IOB）时，此预测的BG曲线表示仅基于胰岛素活性的BG **应该**如何表现。 这里的关键字是 **应该**，因为Spike依靠数学模型来预测未来。 由于人体不断变化，因此，Spike每次接收到新数据（从喵喵读取的读数，来自用户输入的治疗数据等）时都会重新计算预测，这意味着预测也在不断变化。

* **COB (在途碳水化合物):** 一起使用碳水化合物和胰岛素（如果有）来预测BG曲线。
摄入碳水化合物后，该预测线将立即显示S曲线形状，该形状开始平滑（与当前BG趋势一致），然后在大约一个小时后急剧升高，然后趋于平坦。 假设典型的膳食吸收时间约为3小时，然后随着时间的推移进行调整，因为Spike逐渐更多地依赖于实际观察到的碳水化合物吸收数据（通过观察BG趋势随时间变化来确定碳水化合物吸收）。 COB预测曲线只能对BG进行预测，因为它仅限于输入的碳水化合物，与UAG曲线不同。COB预测BG **应该**在存在碳水化合物和/或胰岛素的情况下的行为 。
* **UAG (UnAnnounced Glucose):** Uses "floating carbs" and insulin (if available) together in predicting the BG curve. Unlike the COB predictive BG curve, UAG is not restricted to the carb entry provided by the user. In a way, it doesn’t "trust" carb entries as much. It fact-checks carb entries by looking (retrospectively) at glucose deviation comparisons. UAG is predicting the future BGs based on the slope (rate of change) of actual BGs during periods where Spike believes unannounced glucose is present, either by having meals that are not logged into Spike, by under counting carbs in a meal or by sudden glucose spikes released by the liver into the blood stream caused by stress, the dawn phenomenon, etc. If BGs are rising during a meal or glucose spike and they continue to rise beyond what was predicted on carbs alone (strong deviations happening), UAG is going to carry that prediction forward... regardless of the carbs entered.  And it will carry that forward until the slope stops and things settle down. While COB and IOB predictive BG curves show how BG SHOULD behave based on current trend and IOB/COB alone, the UAG predictive BG curve show how BG IS ACTUALLY behaving based on current trend, IOB/COB and expected/unexpected glucose deviations. The UAG curve is the same as the UAM curve in OpenAPS, it was renamed in Spike for simplicity.
* **ZT (Zero Temp):** Prediction BG curve representing a scenario where a zero temp is given (zero basal insulin). ZT predicts how BG **SHOULD** behave in the absence of basal insulin. Because Spike is not (yet) compatible with logging basal treatments, the ZT prediction curve is only available to OpenAPS users and it is fetched directly from the user's Nightscout site.

Spike will constantly analyze all available prediction curves and  will mark the default one (the one it considers the most relevant/precise at any moment in time) with a purple color. **The default prediction curve is the one used to determine the final predicted BG value** that appears on the prediction pill, fullscreen view, Today Widget, Apple Watch complication and app. The default curve is also the one displayed when activating the _"Single Prediction Curve"_ setting described above.

On the chart screen's header, when the _"Single Prediction Curve"_ setting is disabled and Spike is displaying multiple prediction curves simultaneously, a small legend will be visible and will indicate which curves are being displayed on the chart as well as their respective name and color. Pressing a prediction curve name will show a popup to the user explaining what the curve represents.

[[https://spike-app.com/wiki/images/spikepredictions/01.jpg]]

## Additional Information

When pressing the predictions pill located in the upper right corner of the chart screen, the user is presented with additional sub-pills with various kinds of information aimed at giving the user a better understanding of what is currently going on with its glucose values and trends as well prediction curves. Pressing each sub-pill will show a popup with a brief explanation of what it means. Pressing the pill or popup again will dismiss it.

* **Last Update From NS:** How long ago did Spike fetch prediction's data from Nightscout. _Available to Loop/OpenAPS users only._
* **Time Until High:** Approximate time, in minutes, until BG reaches the user's high threshold defined in Settings > General. This pill is only visible if Spike predicts BG values will fall over the high threshold during the duration of predictions selected by the user. _Available to masters, followers and Loop/OpenAPS users._
* **Time Until Low:** Approximate time, in minutes, until BG reaches the user's low threshold defined in Settings > General. This pill is only visible if Spike predicts BG values will fall under the low threshold during the duration of predictions selected by the user. _Available to masters, followers and Loop/OpenAPS users._
* **Treatments Outcome:** Final BG outcome of all active insulin/carbs treatments. This is the same outcome given by the Bolus Calculator. _Available to masters, followers and Loop/OpenAPS users._
* **Treatments Effect:** The effect that all active insulin/carbs treatments will have on the user's BG (outcome - latest BG reading).
* **BG Velocity Per Minute:** How much BG is rising/falling each minute. This info is also synced to the dedicated Spike Apple Watch app. _Available to masters, followers and Loop/OpenAPS users._
* **Predicted Minimum BG:** Lowest predicted value that Spike has made for the user's future BG. _Available to masters, followers and OpenAPS users. NOT available to Loop users._
* **Predicted UAG BG:** Predicted BG taking only into account the UAG (UnAnnounced Glucose) curve and prediction's duration selected by the user. _Available to masters, followers and OpenAPS users. NOT available to Loop users._
* **Predicted COB BG:** Predicted BG taking only into account the COB (Carbs On Board) curve and prediction's duration selected by the user. _Available to masters, followers and OpenAPS users. NOT available to Loop users._
* **Predicted IOB BG:** Predicted BG taking only into account the IOB (Insulin On Board) curve and prediction's duration selected by the user. _Available to masters, followers and OpenAPS users. NOT available to Loop users._
* **Eventual BG:** Predicted BG after DIA (hours) considering the user's current IOB and COB. _Available to masters, followers and OpenAPS users. NOT available to Loop users._
* **BG Impact:** Current impact of active insulin and currently digesting carbohydrates. It shows what the BG **“should”** be doing, assuming insulin and carbohydrate activity are the only major contributing factors. For example, if BG delta is +2 mg/dL and BGI is +2.6 mg/dL, the user's BG is currently doing what is expect based on current insulin and carb activity (both delta and BG impact are similar). If, on the other hand, the actual BG change (delta) and the predicted BGI are very different, the user's BGs are not behaving as predicted, so the purple prediction line may not end up reflecting reality. This can happen due to incorrect ISF/I:C settings, unlogged or incorrectly logged insulin/carbs or external factors like stress, etc.
* **Deviation:** How much actual BG change is deviating from BG Impact. A high positive/negative deviation number means your BGs are not behaving as predicted, so the purple prediction line may not end up reflecting reality.

[[https://spike-app.com/wiki/images/spikepredictions/04.jpg]]

## Colors

As stated above, Spike supports up to 4 prediction curves. 

* **Default:** When multiple prediction curves are enabled, Spike will always try to determine the most accurate/relevant prediction curve and will use a purple color on it. When using the "Single Prediction Curve" option described above, that curve will also have a purple color. This color can be changed by going to Settings > Chart > Colors > BG Default Predictions. As a rule of thumb, he purple curve is the one Spike believes will reflect your future glucose values.
* **IOB (Insulin On Board):** Spike will always use the same color as the insulin markers on the chart (the markers that appear when the user adds a bolus treatment). The default color is blue and can be changed by going to Settings > Treatments > Insulin Marker Color.
* **COB (Carbs On Board):** Same as above, Spike will always use the same color as the carbs markers (the markers that appear when the user inserts a carb treatment). The default color is orange and can be changed by going to Settings > Treatments > Carbs Marker Color.
* **UAG (UnAnnounced Glucose):** The default color is grey and can be changed by going to Settings > Chart > Colors > BG UAG Predictions. 
* **ZT (Zero Temp):** The default color is baby blue and can be changed by going to Settings > Chart > Colors > BG ZT Predictions. This setting is only available to OpenAPS users that have the "Loop/OpenAPS User" option enabled in Settings > Treatments.

[[https://spike-app.com/wiki/images/spikepredictions/03.jpg]]

## Integration

Although Spike is capable of showing multiple prediction curves simultaneously (IOB, COB, UAG & ZT), it will constantly perform calculations to determine the most relevant prediction curve at that point in time and will apply a purple color to it. Calculations to determine the default prediction line are done every time a new BG reading arrives to Spike and/or a new treatment is added which means the default prediction curve chosen by Spike can change regularly. This default prediction curve is the one used to determine the final predicted blood glucose displayed in the following places:

* **Predictions Pill:** At the top right corner of the chart screen Spike will display the predicted BG for the desired prediction duration. This prediction value has a purple color.
* **Fullscreen View:** Along side IOB/COB values, predictions can be found on the lower part of the screen when activation the fullscreen view.
* **Today Widget:** The same predicted value seen on the chart's prediction pill is also synced to the Today Widget for a quick glance without the user having to unlock his/her device. Whatever prediction duration in selected in Spike settings is the one that will be synced to the Today Widget.
* **Apple Watch Calendar Complication:** Spike can also sync the predicted BG value to the Apple Watch Calendar Complication. This feature can be enabled by going to Settings > Watch. Due to space constrains, besides the current BG value, trend and arrow it will only be possible to also display IOB/COB, predictions or display name along side, not all at the same time.
* **Dedicated Spike Apple Watch App:** Predictions are also synced to the dedicated Spike Apple Watch app and are visible on the upper right corner of the user interface. Predictions (and the rest of the data) can be refreshed by force touching the watch screen and selecting the "Refresh" button. 

## Nightscout Sync

Prediction data (curves and variables) can be uploaded to Nightscout and visualized directly in Nightscout's glucose chart using the Nightscout OpenAPS plugin. This feature is only available to masters. Followers and Loop/OpenAPS users are not allowed to upload any pedictive data.

To use this feature we'll need to enable the OpenAPS plugin in your Nightscout site. Please perform the following steps (we'll use Heroku to exemplify):

Login to your Heroku dashboard using this link https://dashboard.heroku.com and afterwards click on your Nightscout's site name.

[[https://spike-app.com/wiki/images/nightscoutpredictions/01a.jpg]]

Press the "Settings" menu.

[[https://spike-app.com/wiki/images/nightscoutpredictions/02.jpg]]

Press the "Reveal Config Vars" button.

[[https://spike-app.com/wiki/images/nightscoutpredictions/03.jpg]]

Scroll down until you see the ENABLE field and press the pencil icon next to it.

[[https://spike-app.com/wiki/images/nightscoutpredictions/04.jpg]]

Add a SPACE at the end of the field and write the word "openaps" (without quotes). Save your changes.

[[https://spike-app.com/wiki/images/nightscoutpredictions/05.jpg]]

Scroll the page all the way up, click the upper right menu named "More" and click "Restart all dynos".

[[https://spike-app.com/wiki/images/nightscoutpredictions/06.jpg]]

Open Spike on your iOS device, go to Settings > Share > Nightscout, enable the "Upload BG Predictions" option and save your settings.

[[https://spike-app.com/wiki/images/nightscoutpredictions/06b.jpg]]

Now, using your browser, visit your Nightscout site (if it was open previously make sure to refresh it), and activate the openaps plugin by clicking the right upper menu.

[[https://spike-app.com/wiki/images/nightscoutpredictions/07.jpg]]

Now that the plugin has been activated, lets enable the prediction curves by pressing the "..." button at the upper right corner of the screen.

[[https://spike-app.com/wiki/images/nightscoutpredictions/07b.jpg]]

Afterwards you'll be able to visualize your glucose prediction curves on the Nightscout chart.

[[https://spike-app.com/wiki/images/nightscoutpredictions/08.jpg]]

And you'll also have access to a new OpenAPS pill on the upper left side of the screen.

[[https://spike-app.com/wiki/images/nightscoutpredictions/09.jpg]]

A side effect of uploading glucose predictions to Nightscout is that Spike will also upload IOB and COB values. Even if the user uses the oref0 IOB/COB algorithm (Settings > Treatments > Profile), IOB/COB values in Nightscout will stay in sync with Spike. Nightscout will stop doing IOB/COB calculations and instead will rely solely on values uploaded by Spike master.

## Acknowledgements

Special thanks to my friends from the OpenAPS project (Dana Lewis & Scott Leibrand) for the original oref0 algorithm code and for their guidance. <3