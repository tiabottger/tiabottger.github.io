## Spatial error maps
Using the joined bottle dataset I have been using to calculate error metrics, I plotted a spatial representation of error for each station we have observational data for. I am excited about this way of representing the data and think this could be one of my main figures in the poster I am working on. The third panel shows the difference in RMSE between SalishSeaCast and LiveOcean. This visually shows which model has less error-- negative blue values correspond to SSC having less error than LO, while for positive red values LO has less error.

<img width="3000" alt="bottle_2014_DO_station_rmse_error_map" src="https://github.com/user-attachments/assets/6aad92ac-e895-4e66-82fa-d0933808d8bd" />

Several points in Lynch cove and Whidbey basin stand out as having higher error, along with one point in South Sound. The point close to the Skagit river stands out as performing much better in LiveOcean than SalishSeaCast. Susan mentioned having difficulty resolving the shallow Skagit flats.

I have two hypotheses to test for why we see this spatial pattern in error. 

First, the models potentially have more difficulty representing DO in shallower areas. This could be due to the entire water column being more influenced by sediment dynamics at the bed, so complicated biogeochem dynamics like sediment oxygen demand and remineralization become more important that might be simplified in the models. Areas with wetting and drying may be handled differently by the models, which is something I want to look into more.

The other hypothesis is that these are areas that have greater variance in DO. I recognize Hood Canal and Whidbey Basin as being areas where we have low DO at the end of summer, and perhaps these are areas that are more sensitive with changing DO that may not be fully captured by the model. If there is more variability in the data, it is less likely that model data will match it, as things like temporal lags will result in mismatch between model and observations.

### Shallow bathymetry causing error?
<img width="1792" alt="bottle_2014_station_bathymetry" src="https://github.com/user-attachments/assets/8f12b3b8-eeb5-42c6-9b0a-17ebea7e07bb" />

### Models not matching full DO variance?
<img width="3682" height="1827" alt="bottle_2014_DO_station_variance_map" src="https://github.com/user-attachments/assets/a620a465-cb83-4d64-89f4-f0e13bed6a67" />
I want to dig into the question of variance more carefully, here I have plotted the variance for each station which includes depth and temporal variance. So high variance values may be due to stratification or seasonality. Because we have full timeseries for 12 of these stations, I can calculate variance over higher temporal resolution.
