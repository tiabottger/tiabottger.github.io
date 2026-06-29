## Between basin differences - ANOVA tests
## Comparing model agreement between SalishSeaCast and LiveOcean
I went back to my plots comparing regional differences of model output. Aurora created basin masks which I implemented into my code instead of using bounding boxes, to be consistent about where the boundaries between basins are defined. In previous plots I had noticed that SalishSeaCast and LiveOcean seemed to have the most model agreement in Main Basin, with a larger spread in bias values in Whidbey Basin and Hood Canal. To explore the regional differences in model agreement I plotted SalishSeaCast vs. LiveOcean values. These plots visually communicate what I was noticing before, with more scatter in Whidbey Basin and closer 1:1 agreement between models in Main Basin DO. 

<img width="600" alt="image" src="https://github.com/user-attachments/assets/66b68f55-bbd1-4238-87e6-f349fbbd16a6" />

To interrogate these regional differences from a statistical standpoint, I performed a one-way Analysis of Variance (ANOVA) test. For every observation location, I calculated error = SalishSeaCast - LiveOcean. The ANOVA tested whether the average difference between the models was the same across all subbasins, or whether some basins show systematically larger model disagreement than others. The F statistic calculates between-group variance/within-group variance, so a large F value indicates that the basin means differ more than would be expected from within-basin variability alone. The p-value tests whether the observed F statistic could occur if all basin means were equal, so a small p-value indicates that differences among subbasins are statistically significant. With many observations in our dataset, statistical significance is expected even for relatively small basin effects, and it is more useful to look at $\eta^2$ which represents the fraction of total variance explained by basin identity. 

### Dissolved Oxygen SSC-LO ANOVA
**DO: F=22.34, p=2.65e-14, $\eta^2$=0.022**   
An $\eta^2$ of 0.022 for dissolved oxygen means that only about 2% of the variance in SalishSeaCast-LiveOcean DO differences is associated with subbasin identity. So while scatter plots visually show a potential difference between model agreements in subbasins, the statistics suggest that this variability isn't strongly explained by differences between subbasins. 

### Other variables SSC-LO ANOVA
**DIC: F=263.48, p=8.65e-152, $\eta^2$=0.299  
NO3: F=106.23, p=2.31e-65, $\eta^2$=0.298   
NH4: F=103.82, p=6.02e-64, $\eta^2$=0.202   
DIN: F=98.35, p=1.01e-60, $\eta^2$=0.173   
SA: F=95.16, p=7.88e-59, $\eta^2$=0.157   
TA: F=131.29, p=6.44e-80, $\eta^2$=0.155   
CT: F=86.52, p=1.08e-53, $\eta^2$=0.080   
Chl: F=11.26, p=2.40e-07, $\eta^2$=0.025**    

These results suggest that model disagreement is spatially structured for salinity (SA), nutrient (NO3, NH4, DIN) and carbonate (DIC, TA) system variables. For these variables, 15-30% of model differences can be attributed to subbasin location. In contrast, for DO and and chlorophyll, most of the variability occurs within basins, with basin identity explaining very little of the model disagreement.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/8ce707c9-b324-4b77-a356-e695f9571765" />

Looking at DIC, overall SalishSeaCast predicts lower values than LiveOcean. You can see that the data does appear to be clustered differently by basin.

## Comparing model skill by basin
Doing this ANOVA analysis made me curious how much model error comparing to observations can be explained by within basin vs. between basin variability. I conducted a one-way ANOVA for each model, where error = model - observation so the results are about model skill rather than model agreement. Overall, LiveOcean has smaller $\eta^2$ values than SalishSeaCast, particularly for salinity, DIN, DIC, and TA. This suggests that LiveOcean's errors are less dependent on basin and its performance is more spatially consistent. Again, DO and chlorophyll exhibit the least basin dependence, indicating that errors in these variables is not driven by subbasin location. DIC and TA errors are much more basin dependent in SalishSeaCast than LiveOcean. NO3 and CT errors are more basin dependent in LiveOcean than SalishSeaCast.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/ec57d80b-4f09-4e10-8651-c3d012587836" />

### LiveOcean - observations ANOVA
**NH4: F=117.43, p=5.56e-71, $\eta^2$=0.127   
NO3: F=31.23, p=7.70e-20, $\eta^2$=0.106  
DIC: F=7.53, p=6.16e-5, $\eta^2$=0.061   
CT: F=30.34, p=3.61e-19, $\eta^2$=0.056  
SA: F=12.16, p=6.90e-8, $\eta^2$=0.041  
DIN: F=12.39, p=4.84e-8, $\eta^2$=0.022  
DO: F=2.33, p=7.23e-2, $\eta^2$=0.022  
TA: F=2.36, p=7.06e-2, $\eta^2$=0.021  
Chl: F=1.50, p=1.13e-1, $\eta^2$=0.005**

### SalishSeaCast - observations ANOVA
**TA: F=34.03, p=3.77e-20, $\eta^2$=0.170  
DIC: F=30.66, p=2.93e-18, $\eta^2$=0.162  
NH4: F=134.27, p=1.93e-80, $\eta^2$=0.147  
SA: F=36.75, p=4.20e-23, $\eta^2$=0.133  
DIN: F=49.41, p=5.58e-31, $\eta^2$=0.059  
NO3: F=30.32, p=2.86e-19, $\eta^2$=0.040  
DO: F=6.36, p=2.75e-4, $\eta^2$=0.023  
CT: F=10.25, p=1.07e-6, $\eta^2$=0.022  
Chl: F=3.17, p=2.34e-2, $\eta^2$=0.009**




