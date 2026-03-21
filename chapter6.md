# Chapter 6: Conclusion

[ < Back to Chapter 5 ](chapter5.md) | [ Master Index ](dissertation.md) | [ Next: Appendix 1 > ](appendix1.md)

---

### 6.1 Research Summary and Core Contributions

#### 6.1.1 Motivation and Objective
This study makes significant strides in filling current research by building a bridge to link the physical world and financial market and using XGBoost+ SHAP value methodology to reveal the complex relationship and quantify the influence at the global level and local level, answering the questions of whether weather-related risk impacts the financial market from both what and how aspects.

The primary motivation of this research is to address the challenges posed by the increasing frequency and intensity of extreme weather events, which are exacerbated by climate change and global warming, and that threaten both global food security and financial stability. Although numerous studies have already examined these two aspects in isolation, without an integrated framework that can link them together, a comprehensive understanding of how climate change will impact society and the economy globally remains elusive. 

The international trade system and globalisation of the financial market have already reshaped the world economy. Any small action in the physical world can lead to significant consequences in the financial and economic systems, as described by the butterfly effect. This research aims to construct an analysis framework which covers the whole chain of transmission from shock in the physical world to the futures market, systematically addressing the following four core research gaps identified in the literature review chapter:

* **Methodology gap:** Overcomes the data noise and incomparability problems due to heterogeneous spatial-temporal frameworks based on administrative divisions and Gregorian calendar months.
* **Interaction & non-linearity gap:** go beyond the traditional linear model limitation, provide an in-depth investigation for complex non-linearity relationships driven by compound events and threshold effects 
* **Integration gap:** bridge the broken chain of the physical world and financial markets.
* **Explainability gap:** meeting the challenges of "black-box" characteristics of machine learning models, improving the model explainability and informative strategies.

#### 6.1.2 Analysis Framework and Methodology Contribution
This study designed and implemented a two-stage integrated research framework:
1. The physical impact model focuses on the quantitative impact of abnormal weather events on crop yield.
2. The financial model utilises core weather-related risk factors, analyses the mechanism by which physical shocks are transmitted to financial markets, and then is absorbed and reflected in pricing fluctuations.

We conducted a systematic standardised procedure for addressing the heterogeneous spatial-temporal problem: firstly, developed a data-driven methodology, set a specific 24 × 15-day periods for each country increased the comparability between different countries, then based on various weather statistic information, we adopt a K-means clustering algorithm, building high level homogeneous climate-grain zones to reduce the geographic noisy due to the different climate weather patterns within the administration divisions.

After comparing model performance with basic models, we ultimately adopted the XGBoost + SHAP values analysis method for both model building and explanation. XGBoost has better functions for capturing non-linear relationships among our high-dimensional datasets. Additionally, the built-in sparsity-aware algorithm effectively handles the missing values in the table of abnormal weather events. Moreover, combined with the optimised TreeSHAP, this methodology provides accurate, consistent, and comprehensive explanations that cover both global and local attribution levels.

### 6.2 Key Findings

#### 6.2.1 Core Findings of The Physical Impact Model
The failure of the baseline model revealed that the linear relationship assumption could not explain the dynamic complexity of interactions among the various weather features, which justified the final model choice. Based on the Advanced machine learning model XGBoost and a strong explanation tool: TreeSHAP, we discovered the three key principles of crops' response to weather-related risks: 

* **Time sensitivity:** Different crops have varying sensitivities to high-impact weather factors. This research presents a quantitative methodology to validate the conclusions of previous studies on time series, including the mismatch between optimal weather conditions and key growth stages, which leads to yield reductions. In addition, we utilise the SHAP value to not only identify the sensitive time window but also to accurately quantify the contribution of each feature in a specific period to the yield estimation result. For example, the yields of wheat and maize have been significantly impacted by the legacy effects of last winter's weather. At the same time, rice and soybeans are susceptible to specific time windows of key growth stages.
* **Condition dependence:** the effect of compound weather events is not simply the sum of linear additions. This research utilises the SHAP value to reveal the interaction mechanisms behind the complex, non-linear relationship, explaining and quantifying the integration influence of compound events, which adds valuable insight to previous qualitative analyses. Our key findings, along with the different interactions, not only confirm previous findings but also contribute to the current research gap in understanding the complex response patterns of various crops to abnormal events. Moreover, it provides a systematic comparison between various crops under a complete set of other weather events.
* **Regional Baseline:** The regions' inherent natural endowments and climate baselines are the key moderators. This study offers an in-depth examination of a common topic: regional variations in the physical effects of weather-related risks on agricultural production. It goes beyond a qualitative description, quantifying and revealing how the regional baseline works as a moderator that changes the direction, intensity, and interaction of abnormal weather events.

#### 6.2.2 Core Findings of The Financial Transmission Model:
1. **Identified the Dual-driven characteristics of market price fluctuations.** The primary drivers are the long-term market inertia (reflected by the Close_lag), which is the most significant influencer of price predictions, with much higher SHAP values than other factors. However, the aggregate influence of weather factors cannot be ignored; their combined contribution exceeds 30%, which constitutes the second most significant driver factor.
2. **Evidence of financial market efficiency and forward-looking:** the impact of weather forecast information (lead features) generally exceeds that of the occurred weather factors (lag features). Especially for the world's largest economy, the USA, the SHAP value of the forecast temperature is nearly twice that of the old information.
3. **Revealed the complex risk pricing mechanism:** the market response for weather risk shock is also full of non-linear relationships, reflecting threshold, amplifying and buffering effects. The combined negative factors will amplify the adverse influence, but favourable factors in other regions may buffer or offset the downward pressure from both the supply and demand sides.

### 6.3 Limitations of This Study

#### 6.3.1 Methodology level

* **The systematic bias of the growing season algorithm** The algorithm, based on the daily average temperature curve crossing the preset threshold, exhibits good performance in high-latitude regions with distinct seasons. However, it cannot identify the clear start and end points of the growing season for subtropical and warm-temperature zones (for example, the middle and lower reaches of the Yangtze River in China), which have more complex climate models. This algorithm bias leads to those regions being systematically filtered out in the data preparation stages; the following model build is based on the region samples with relatively simple climate and weather patterns. Hence, this led to a geographic bias in our conclusion, limiting the generalizability of our findings to low- and middle-latitude regions.

* **The generalisability of the Standardised 24×15-day periods**
The standardised 24×15-day periods-division method, have not been adjusted for adverse seasonality of the Southern Hemisphere, potentially leading to mismatch of weather events with the core growth stages of crops in countries like Australia, may misalign with the weather factors impacting on those countries, in addition, this framework also cannot capture the multi growth seasons in tropical regions and semi-tropical regions, this lead to compromise model accuracy.

#### 6.3.2 Data level

* **The inherent limitations of the first model (Yield) are the estimation nature of the target variables.** Iizumi's global yield information is an estimate of production based on a downscaling model that integrates satellite remote sensing and statistical data. This means that these data are not actual farm field data, indicating that the research's model study target is to estimate another model prediction, thereby causing risks of error propagation and learning model artefacts.

* **The static assumption of this yield information dataset imposes further limitations.**
This model employs a 2000 static planting area distribution for model building, which fails to capture the dynamic changes in farm field utilisation due to urbanisation, agricultural development, and climate adaptation. Thus, the model cannot capture the yield change caused by the shifting of cultivation zones, which may lead to less accurate attribution analysis.

* **Another limitation is the large-scale weather information data.** The primary dataset of ERA5-Land is a gridded dataset with an 11 km resolution. Although this is sufficient to support a global-level comparison, it may average or smooth the changes in local region characteristics, such as microclimate, Terrain, and slope direction, which are also crucial for crop planting.

* **A further limitation of the dataset is its shorter period of coverage.** The physical shock model utilised a dataset from 1990 to 2016, which lacks the most recent data. However, recent data may exhibit significant differences from previous periods due to the acceleration of climate change resulting from the rapid accumulation of CO2 levels in the atmosphere. Hence, the model might lose its most valuable conclusions. The financial model dataset only covers the period from 2008 to 2020, omitting the pre-crisis and post-COVID periods, both of which exhibit different patterns of market change. This omission compromises the model's ability to capture the trends of long-term cycles and structural changes, thereby influencing the long-term stability and generalizability of the model's conclusions.

#### 6.3.3 Model specification level 

* **The omitted variable in the agricultural impact model**
This research focused on weather factors and failed to incorporate other key influence factors, such as soil conditions and quality, irrigation, fertiliser applications, and changes in crop varieties, all of which are controlled by agricultural technology. In a real-world scenario, those non-weather factors are the primary or essential moderating factors of agricultural yield; omitting these might lead to overestimating or underestimating the influence of weather factors.

* **The simplification of driver factors for the financial transmission model**
The second-stage model is more focused on weather risk transfers from the physical world. However, in an actual scenario, the financial market is heavily and directly influenced by macroeconomic policy, individual market player behaviours, and liquidity levels, which represent the inherent financial drivers. This model has not accounted for the factors that impact it, which will limit its explanatory ability, especially in understanding the significant market turning point.

### 6.4 Avenue for Future Research

#### 6.4.1 Methodology Refinement and Improvement
Future research should continue to refine the algorithm for defining the growing season, which is adaptable to multiple regions with both complex and simple seasonal patterns. The new algorithm should not only consider temperature changes but also incorporate additional weather factors, such as rainfall rhythms, changes in photoperiod, and soil moisture, combined with a specific crop's phenology knowledge base, to build a regional adaptation multidimensional model.
Prioritising the time frame is another field the future study should focus on. For the Southern Hemisphere, it should align with the period of the Northern Hemisphere or build a more accurate period division matched to the growing stage of a specific crop; for multi planting seasons, it should separate the different seasons' yield information, like spring wheat, Winter wheat, major season rice, second season rice, etc., to capture risk factors more dynamically.

#### 6.4.2 Dataset Level Integration and Validation
The future study should overcome the limitation of current data by utilising a dataset with higher quality and more dynamic information. The future model should investigate and cross-validate with the other global yield dataset, which contains dynamic farm field statistics data, especially for data-rich regions like the USA and the EU, conduct a regional validation process, utilising the officially published high-precision yield data, which is based on the actual field surveys, to test and align the global model performance.

#### 6.4.3 Analysis Framework Level Expansion and Synthesis
The agricultural impact model should be extended by incorporating more non-weather factors that represent the agricultural technical level and are more controllable. Setting these factors as static or dynamic features will further investigate the interaction of non-weather factors with weather factors, providing a comprehensive view of the aggregate impact on crop planting.

The financial model should be further developed by accounting for more financial inheritance factors like exchange rates, interest rates, PMI, VIX and holding report to get full and better understanding of market movements, and also combined with the change of international trade price volume and patterns to investigate the both future market and spot market of agricultural commodity to get information of how different markets linked internally and transfer information and risk factors.

Ultimately, the Future model should aim to internalise human behaviour, incorporating climate adaptation behaviours such as upgrading and changing crop varieties, adjusting planting dates, investing in irrigation facilities, and investors adjusting their trading strategies as internal features. Through the above model adjustment, we can conduct more accurate and comprehensive evaluations and estimations of agricultural climate risk.

---
[ < Back to Chapter 5 ](chapter5.md) | [ Master Index ](dissertation.md) | [ Next: Appendix 1 > ](appendix1.md)
