## Bottom DO with SSM

Salish Sea Model (PNNL version) displays a very different timing in bottom hypoxia than SalishSeaCast and LiveOcean, notably having a large hypoxic area in January while the other models have zero at this time of year. The timing is suspicious because it looks as though the amount SSM is shifted relative to the other models as hypoxic area ramps up later in the year is about the amount of time that there is hypoxia at the beginning of the year. I can't imagine how the timing could have shifted during my extraction however. Looking at spatial maps of bottom DO over the year shows the same signal of hypoxia in January. 

To investigate this timing further I plan to look at other variables such as temperature and salinity and see whether their seasonality also appears shifted. I will also take a look at other years and see whether January hypoxia is present in SSM. I am curious whether the Ecology version of SSM will exhibit January hypoxia-- I wonder if there are differences in how the models were initialized given that the PNNL SSM data on the portal seems to be from a long hindcast beginning in 2013 while the Ecology version is run on itself several times for spin-up and only run for the year 2014.

<p style="text-align:center;"><video src="https://github.com/user-attachments/assets/c6b08dd0-8407-4d55-807b-913eafbd89ea" controls="controls" style="max-width: 800px;"></video>
 </p>

Here is the same animation using a colormap that displays hypoxia (DO < 2 mg/L) in red.

<p style="text-align:center;"><video src="https://github.com/user-attachments/assets/15860c65-9cf1-451d-9137-425f45bfd6ca" controls="controls" style="max-width: 800px;"></video>
 </p>

### Average bottom DO

The spatial pattern of bottom DO for Salish Sea Model looks similar to LiveOcean, with the lowest DO in Hood Canal. As seen before, SalishSeaCast is quite different, with the most hypoxia in Whidbey Basin. Note that the hypoxia SalishSeaCast reports in Port Townsend bay off of Indian Island (in the north near Admiralty Inlet) is artificial as a result of the grid not having connectivity on the side of the island and forming a terminal inlet there when in reality it is not one. 

<img width="1000" src="https://github.com/user-attachments/assets/75f8b4bd-29f9-4d05-901a-7826c77d3840" />

### Comparison to Khangaonkar et al. 2018

Note that we don't believe the SSM model used in Khangaonkar et al. 2018 is the same as the data available on the portal, which follows Khangoankar and Yun 2023 in being a model run over multiple years.

The hypoxic area timeseries reported in Khangaonkar et al. 2018 follows timing more similar to SalishSeaCast and LiveOcean, without having a January hypoxia signal. The magnitude of hypoxic area is much larger, although the domain is larger as well including the full SSM domain while I have masked to just the Puget Sound domain. There is significant hypoxic area in Bellingham bay, Samish bay, and East Sound that is not included in my calculation. However, this doesn't seem to explain the entire magnitude difference.
  
<img width="700" src="https://github.com/user-attachments/assets/57d3a251-029b-462a-9c0c-e0a556f67b8a" />

Comparing hypoxic occurrence, the map reported in Khangaonkar et al. 2018 predicts far more hypoxia than any of the models for which I have calculated it. Note the color bar has been scaled the same. I suspect that Ecology's version of SSM will look more similar to what is reported in Khangaonkar et al. 2018. 

<img width="1000" src="https://github.com/user-attachments/assets/891124e8-94c2-42f7-936b-d1f6791c02df" />

### Sensitivity to spin-up

I am a bit concerned about this difference between Khangaonkar et al. 2018's results and our model results given the sensitivity bottom DO has to spin-up. Khangaonkar et al. 2018's version of the model seems to have been run in a unique way compared to the other models, as "the simulation was then repeated using year-end results as the restart initial condition" in the same/similar way as it is run by Ecology. We know there are spin-up concerns in 2014 for LO and SSC, and if this SSM version was initialized in 2013, there may be spin-up concerns as well. 

To demonstrate this sensitivity, I plotted the hypoxic occurrence for LiveOcean cas7_t1_x11ab, the long hindcast of LiveOcean initialized in 2012, compared to the hypoxic occurrence for the more spin-up run of cas7_t1y14_x11ab for which 2013 was run on itself for a total of 3 times before starting the 2014 run using its initial condition. 

<img width="1000" src="https://github.com/user-attachments/assets/9ba1b0cf-b052-4195-9761-c0e2fed1edab" />
