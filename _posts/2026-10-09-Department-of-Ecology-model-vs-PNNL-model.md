## Department of Ecology model vs. PNNL model

Ecology has run Salish Sea Model for the year 2014 (also 2000, 2006, and 2008). We think the way that they have configured the model should lead us to treat it as a separate model as Salish Sea Model, and include it in the intermodel comparison as a fourth "management model" for the year 2014 only. The reasoning for using 2014 is described as follows: "Ecology selected 2014 as the model year for Opt2 PSNSRP load variations scenarios because it is a more recent year that includes the Brightwater facility (a newer WWTP 
that discharges to Main Basin that came online in September 2011). Additionally, previous analysis had shown that 2014 was an average year in terms of residence time for the Central Basin (PSEMP 2016). However, in this phase of the work, we found that overall, at the Puget Sound scale, 2014 is the year with the fastest winter flushing time within the set of years considered." 

The configuration and model results are described in the Puget Sound Nutrient Source Reduction Project (PSNSRP), [Figueroa-Kaminsky et al. 2025](https://apps.ecology.wa.gov/publications/summarypages/2503003.html). The model output is available for download on the [Department of Ecology website](https://fortress.wa.gov/ecy/ezshare/EAP/SalishSea/SalishSeaModelBoundingScenarios.html). Some notes from reading this report:

- Phase 2 Optimization Scenarios (Opt2) are described in the 2025 report and include model improvements from Phase 1 Opt1 described in the 2021 Tech Memo, Ahmed et al. 2019. I believe Opt1 uses the same base model as Khangaonkar et al. 2018. Opt2 includes a switch to FVCOM2.7 and ICM4 from ICM2.
- The biogeochemical model is based on CE-QUAL-ICM. The updated version, ICM4, has corrected photosynthetically active radiation (PAR) daily distribution and the capability to use variable bottom friction.
- The 10 year spin-up used by Ecology is motivated by allowing the sediment fluxes to stabilize.
- Some parameters have changed from those published in Khangaonkar et al. 2018. Detritus settling velocities reduced from 5 m/day to 2.5 m/day. Half-saturation concentration of ammonium ion required for nitrification increased from 0.5 g N/m3 to 0.75 g N/m3. Photosynthetic rate of algal group 2 increased from 350 to 450 g C/g Chl/d, and initial slope of photosynthesis vs. irradiance curve for algal group 1 decreased from 12 to 8 g C/g Chl.
- Ecology performed grid masking different from SSM (Appendix D uses the wording "reviewed SSM grid masking". They masked nodes with elevations of 4 m or less during ebb tides.
- It seems like Ecology used data to "calibrate" the model? Not sure what this entails, but there is a sentence when describing observations used for model skill that states: "these observations are completely independent of the data used for SSM calibration."

---------------------------------------------------

<img width="800" src="https://github.com/user-attachments/assets/b87b860c-fd5e-4c98-9314-730fdc3bc3fa" />


Fig. 1: Property-property plots of SSM PNNL model (green) compared to SSM Ecology model (purple).

<img width="1000" src="https://github.com/user-attachments/assets/8b3d1b90-058a-48ce-93c3-560cbb93f8b6" />     

Fig. 2: RMSE by station comparing SSM PNNL model to SSM Ecology model.

- DO RMSE is slightly lower for the Department of Ecology SSM model than the PNNL model (RMSE 1.342 compared to 1.447). While DO is biased slightly low (-0.1) for the PNNL model, the Department of Ecology model has a bias of 0.
- While the PNNL model overall has larger RMSE, there are some stations for which the Ecology model has higher RMSE. RMSE is most notably improved in Ecology's model in Lynch cove.
- Salinity predictions are slightly improved in Ecology's model, while temperature has slightly worsened. There is a larger negative bias for temperature. Colder water is more soluble to oxygen, so this might be linked to why DO went from biased slightly low to having a bias of 0.
- Nitrate predictions have improved (RMSE 5.1 compared to 5.6).

*From previous version which converted using nitrate molecular weight instead of just nitrogen*   
- *Nitrate is extremely different between the two models. I wonder if this is a misunderstanding of the variables reported in Ecology's model output. While the value was reported as concentration of NO3 in mg/L (which I then converted to uM), Figueroa-Kaminsky et al. reports an RMSE for NO3-NO2. This is worth looking further into, especially given that the half-saturation concentration of ammonium ion required for nitrification was changed. The half saturation concentration was increased, which would potentially result in higher ammonium and lower nitrate concentrations.* 


### Comparing skill scores to reported values

Khangaonkar and Yun 2023 report a DO RMSE of **0.90** for 2014, using monitoring data collected by Ecology's Marine Monitoring Program. Figueroa Kaminsky et al. 2015 report a DO RMSE of **0.82** (pg 29), using Ecology long-term monitoring stations, South Sound Study stations, King County marine monitoring stations, and NOAA and UW marine monitoring stations (station locations mapped in Appendix D). Here N, the number of data points, is reported as 97,566. The N that I used to calculate RMSE is only 1,947. There are a couple of reasons why this number is so much higher than the observational dataset we've been using. I believe the main reason is that this **includes CTD measurements**, while we have been using bottle samples only. This means some stations have many more measurements because they include full DO profiles. Ecology also used stations over the entire domain, rather than masking to only include the Puget Sound. It is possible that they are including more or different stations than we are as well, although I need to investigate this further. My initial check doesn't point to this being the case-- the number of unique stations in the Ecology matched observation dataset is 86, while our number of unique stations (not masked to the Puget Sound) came out to 271. I am slightly skeptical of this count, as we have noticed overlapping points in our plots before and I think it is possible that some stations have been logged multiple times with different identifiers or slightly shifted lat lon coordinates.

Department of Ecology has published their dataset for observations matched to model output, so I could use this dataset to match with model output and compare skill scores using the same observational data. The main limitation here is that the file does not include lat lon coordinates for stations, however it does include the corresponding SSM node, so I could back-calculate lat lon coordinates for matching with LiveOcean and SalishSeaCast.


### Questions to follow-up on
- The Salish Sea Model data available at the data portal cites Khangaonkar et al. 2018 and Khangaonkar and Yun 2023 for more details. I assume this means the version run is following the parameters and rates listed in Khangaonkar et al. 2018? Khangaonkar and Yun 2023, which use Salish Sea Model results from 2013-2020 state "during this effort the hydrodynamic component of the model was upgraded from FVCOM2.7 to FVCOM4.3 and recalibrated over a multi-year simulation from 2013-2020." I am not sure if it is using the updated biogeochemistry module (ICM4)? I think the results on the data portal are from the long hindcast version in Khangaonkar and Yun 2023. 
