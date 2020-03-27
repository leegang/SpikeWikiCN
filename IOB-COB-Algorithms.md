## Algorithms

Since version 3.5.0, Spike supports two IOB/COB algorithms:

* **Nightscout:** A simpler, more basic algorithm. Calculations are less CPU intensive but also less accurate. Peak insulin time for all insulins will always default to 75min when calculating IOB, following a bilinear model. COB will be calculated assuming carbohydrates are absorbed in a linear fashion which can be imprecise/misleading. This is the default algorithm in Spike.

* **OpenAPS(oref0):** Part of the oref0 algorithm ported from the OpenAPS project. The algorithm has been heavily modified and optimized to work with Spike. It supports bilinear and exponential insulin models when calculating IOB, allowing the user to select custom peak insulin times (exponential model only), providing greater accuracy. COB is calculated based on glucose deviation which is analyzed by constantly looking at the user's glucose trend after a carbohydrate treatment (up to 6h afterwards) providing greater precision at the cost of slightly more CPU cycles. **Loop/OpenAPS users will still need to select the "Loop/OpenAPS User" option in Settings -> Treatments.** The current oref0 implementation in Spike is NOT (yet) suitable to work offline for OpenAPS/Loop users (calculations will differ due to temp basals not being accounted for). By selecting the "Loop/OpenAPS User" option Spike will NOT calculate IOB/COB internally and instead will fetch calculations directly from the user's Nightscout site guaranteeing that both Spike and the rig stay in sync. Users with recent iOS devices are **HIGHLY** advised to use the OpenAPS IOB/COB algorithm.

The preferred IOB/COB algorithm can be selected by going to Settings > Treatments > Profile. Have in mind that the OpenAPS algorithm requires that ISF (Insulin Sensitivity Factor) and I:C (Insulin to Carbohydrate Ratio) be configured in Spike. This can be done at the bottom of the same settings screen.

[[https://spike-app.com/wiki/images/algorithms/iobcob/01.jpg]]

## Insulin Models

Spike supports 2 insulin models: bilinear and exponential. Insulins can be added and models configured in Settings > Treatments > Profile.

* **Bilinear:** A simpler model, almost identical to the one used by the Nightscout algorithm, which only takes duration of insulin action (DIA) as an input parameter. This is a non-curve insulin activity model available in both the Nightscout and OpenAPS (oref0) algorithms.

[[https://spike-app.com/wiki/images/algorithms/iobcob/02.jpg]]

* **Exponential:** A more advanced model that can be customized (within legal limits) to better fit individual needs. It takes both DIA and peak as input parameters. This model is more accurate than the bilinear one and more closely aligned to how the human body absorbs insulin since most insulin types reach their peak performance and decay along a curve. The exponential model requires the user to set a longer DIA than the bilinear one because it creates a more realistic insulin tail. If the user uses a DIA of, let's say, 3h with the bilinear model or Nightscout algorithm (also bilinear) then it would probably need to set a DIA of 4-5h with the exponential model, which is in line with empirical data released by most insulin manufacturers. Spike provides several different presets already customized to fit most commercial insulins. The Rapid-Acting presets are suitable for Novolog, Novorapid, Humalog and Apidra insulins while the Ultra-Rapid presets will better fit Fiasp. Presets can be used as is or as a base template for further customization. Besides DIA, the exponential model also allows customization of peak time, which is the duration (in minutes) until insulin action reaches its peak activity level. The exponential model is available only when using the OpenAPS (oref0) algorithm.

[[https://spike-app.com/wiki/images/algorithms/iobcob/03.jpg]]

Any modifications to DIA and/or peak can be visualized, live, by looking at the insulin curve plotted in Spike.