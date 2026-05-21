My first look into model vs. observational data was creating property-property broader plots exploring broader statistics and model skill metrics for SalishSeaCast and LiveOcean. Now I am taking a closer look at timeseries data to compare observations to model output. I am looking for whether there are any spatial trends or differences between stations, and what the timeseries generally show. 

Starting with dissolved oxygen (DO), we have bottle measurements at three main depths: -30.5 m, -11 m, and -1 m. Some stations have deeper measurements, but these are consistent across most stations so I'll look at these for now. In the property-property plots, LiveOcean performed worse than SalishSeaCast at depth whereas shallow values performed better. 

At the surface (-1 m), LiveOcean most closely tracks DO observations. SalishSeaCast is biased low, although appears to predict DO better at Main Basin sites where it tracks very closely with LiveOcean results. The surface peaks in DO are underpredicted. The depth of observations is matched to the closest sigma layer in model data, which may be over a larger depth range and therefore smooth out these peaks.
<img width="1300" alt="image" src="https://github.com/user-attachments/assets/40c67f4e-2688-44db-aad4-906e74b84bc2" />

At mid-depth (-11 m)  both LiveOcean and SalishSeaCast are biased low. At the Whidbey Basin sites SalishSeaCast captures a larger spike in summer of 2017 than LiveOcean. There seems to be the closest agreement at Main Basin sites.
<img width="1300" alt="image" src="https://github.com/user-attachments/assets/9ffafbd6-ee70-4e58-96f7-31392302b028" />

At depth (-30.5 m) LiveOcean captures Whidbey Basin sites well but is generally biased low. At site HCB004 in Hood Canal, which goes hypoxic, there are the biggest differences between models and observations. LiveOcean appears to perform better at depth in Whidbey Basin than Salish SeaCast.
<img width="1300" alt="image" src="https://github.com/user-attachments/assets/abc4f856-c207-4ecf-a58c-afc0fb0ead8f" />


