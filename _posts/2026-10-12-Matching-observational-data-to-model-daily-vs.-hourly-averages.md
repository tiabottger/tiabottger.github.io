## Matching observational data to model daily vs. hourly averages
LiveOcean has model output saved as daily averages (with the exception of 2017, for which we have hourly average output). A question that has repeatedly come up is how matching observational data, which occurs at a point in time, to a daily average value might be introducing error. For sites that have larger fluctuations in DO concentrations throughout the day and more variability there might be larger error statistics as a result of the daily average matching. 

Salish Sea Model has hourly output available on their data portal. A simple first test to investigate how daily averaging might be introducing error is to compare the matched hourly average data to matched daily average data for Salish Sea Model. 

I calculated the RMSE for each station using the daily average matched data alongside the hourly average matched data.

<img width="3000" src="https://github.com/user-attachments/assets/35721368-4a69-4ab0-9514-1e14978725bc" />

These results are somewhat surprising. The observations matched to a daily average of model output have lower RMSE overall (1.401 mg/L) than the observations matched more closely to hourly values (1.447 mg/L). Looking at the plot of daily - hourly RMSE, most of the values are negative suggesting that the RMSE for the hourly matched data is larger than the daily matched data. The difference between daily and hourly averages including all stations is -0.046 mg/L.

This suggests that the averaging done over a daily timescale doesn't introduce error, but may produce a value that is a closer match to observations by including more information. The difference between the daily and hourly matched model values is not very large. 

### Salinity and temperature

<img width="3000" src="https://github.com/user-attachments/assets/87796cd1-5085-42db-b33a-4f9962ad969a" />

<img width="3000" src="https://github.com/user-attachments/assets/76d3c0e7-a916-4db5-a48f-245f420a4865" />

Salinity and temperature similarly don't have a large difference between values matched on model hourly vs. daily averages. Again, the daily average RMSE is slightly lower. This suggests that tidal variation is not significant, because if it were we would expect the observations to better agree to model values at the same hour. It's possible that these tidal fluctuations on a shorter-term scale are relatively small compared to background variability. If all models are reasonably representing tides I could hypothesize that the difference in RMSE is consistent across models.

RMSE weights large differences more heavily than smaller ones, so if scales larger than a day are mattering the most then hourly differences won't matter. I could compare RMSE differences to the mean absolute error, which treats all errors on a linear equal scale.

As a next step, I might try and answer *how much variability does daily averaging remove?* This would require doing a full hourly extraction however. I could create bounds based on a daily minimum or maximum, or some kind of percentile bounds, for each station. I could also compare this to a similar analysis using 2017 hourly data for LiveOcean. I might focus on 2017 because I have model output for all models for this year, and look at 4ish station extractions. 
