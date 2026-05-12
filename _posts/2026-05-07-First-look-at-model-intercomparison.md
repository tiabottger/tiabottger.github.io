I created property-property plots using the script `plot_multi.py` which I modified to plot LiveOcean data output from the cas7_t1_x11ab run and SalishSeaCast (ssc) data compared to observations. Note that Salish SeaCast does not have a chlorophyll variable and instead has output for diatoms ("diat") and flagellates ("flag"). Salish Sea Cast also has silicon which LiveOcean does not.

The observational dataset includes bottle data described in [LO/obs](https://github.com/parkermac/LO/tree/main/obs). To create the combined dataset, model data has been interpolated to the observation depth using the nearest model vertical index.

Shallow is defined as all depths above -30 m, while deep is defined as all depths below 30 m. Salish Sea Cast is shown in blue while LiveOcean is shown in red. 

### 2015
<img width="1200" alt="bottle_2015_all_deep" src="https://github.com/user-attachments/assets/bd4853e8-7725-4c72-96ba-057d7fd9d4b8" />
<img width="1200" alt="bottle_2015_all_shallow" src="https://github.com/user-attachments/assets/c32556df-8b27-4dfb-928c-ca868f42a49d" />

### 2016
<img width="1200" alt="bottle_2016_all_deep" src="https://github.com/user-attachments/assets/5481d127-c350-48b2-88e2-66c39a22b350" />
<img width="1200" alt="bottle_2016_all_shallow" src="https://github.com/user-attachments/assets/2585f020-61dd-442f-9ee0-76e7c8748beb" />

### 2017
<img width="1200" alt="bottle_2017_all_deep" src="https://github.com/user-attachments/assets/4b482b8c-6cc8-4adf-991a-73736e2e6e38" />
<img width="1200" alt="bottle_2017_all_shallow" src="https://github.com/user-attachments/assets/98623b93-1e33-4af3-88de-035b11b6d39f" />

## Initial Thoughts
- DO does simularly well for both models. It is biased low for all but shallow 2016 when LiveOcean has a bias of 0.6. At depth, LiveOcean performs slightly worse by a couple of values. For shallow comparisons, LiveOcean performs significantly better, cutting the bias of SalishSeaCast approximately in half for 2015 and 2017, and having a bias of 0.6 compared to -13.1 for 2016.
- Nitrate (NO3) was consistently biased higher for LiveOcean and as a result DIN, the sum of ammonium and nitrate was also biased higher. Ammonium stands out as having large differences between models, with SalishSeaCast biased high while LiveOcean was biased low
- The models perform best for absolute salinity (SA) and conservative temperature (CT), with more scatter in the shallow plots than at depth. This is likely because in shallow water, there is higher spatial variability such as where incoming river plumes substantially change salinity on a scale that might not be captured at the model grid cell resolution. We see this in the fanning out of salinity points especially at lower salinities where freshwater spatial variation may not be perfectly captured.
- LiveOcean is biased very high for dissolved inorganic carbon (DIC) and total alkalinity (TA). SalishSeaCast is biased low for dissolved inorganic carbon.
- Chlorophyll is all across the map. Matching chlorophyll values at exact timepoints and depth is hard because phytoplankton vertically migrate on daily cycles, with different phytoplankton species occupying different niches so there is tremendous variability. On average as an integrated quantity we must capture chlorophyll well enough because we are able to model DO well.
