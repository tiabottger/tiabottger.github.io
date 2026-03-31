## LiveOcean Hypoxic area and volume comparison figures

As part of the intermodel comparison discussion we would like to take a closer look at the hypoxic area and volume by subinlets in the Puget Sound. This is motivated by the question of where and when the most hypoxia occurs, and what differences there may be between LiveOcean and the Salish Sea Model.

Aurora has created a script to run a timeseries of hypoxic volume from 2015-2020. This reads in a [box extraction](https://github.com/parkermac/LO/tree/main/extract/box) (using `LO/extract/box`) that effectively crops the raw LiveOcean output to a smaller domain to make these (still rather large) files easier to work with. Aurora also further processed the files into netCDFs that contain time-variable bottom DO concentration, thickness of the water column, and thickness of the water column that is <= 2 mg/L, <= 1 mg/L and <= 3 mg/L. I used Aurora's [scripts](https://github.com/ajleeson/LO_user/tree/main/hypvol_for_intrmdl_cmprsn) as a jumping off point.

The following plots are a timeseries of the hypoxic volume and hypoxic area (the bottom grid cell area for cells <= 2mg) from 2015-2020 for loading runs including WWTPs.

<img width="1200" alt="hypvol_subbasin_comparison_fig" src="https://github.com/user-attachments/assets/aa69ba8f-ffea-4458-a402-64e91944b53f" />   
Fig 1. Hypoxic volume by subbasin timeseries

<img width="1200" alt="hyparea_subbasin_comparison_fig" src="https://github.com/user-attachments/assets/3690bbfb-e183-46c8-ae9f-3a79b8066dfb" />
Fig 2. Hypoxic area by subbasin timeseries

-------------------------
    
Similarly to the Salish Sea model, Hood Canal accounts for far and away the largest extent of hypoxia. Breaking this down by year, I also summed the total hypoxic area by subbasin as a percent of total hypoxic area for the entire Puget Sound.

<img width="1200" alt="hyparea_subbasin_percent_2015_fig" src="https://github.com/user-attachments/assets/6412f7c6-c957-4e6b-9e58-262bcbbd0952" />
<img width="1200" alt="hyparea_subbasin_percent_2016_fig" src="https://github.com/user-attachments/assets/d8f5a2ef-4910-449d-a460-e4b792fbe700" />
<img width="1200" alt="hyparea_subbasin_percent_2017_fig" src="https://github.com/user-attachments/assets/46195b61-c7d1-4650-81fb-dbc89bdb095e" />
<img width="1200" alt="hyparea_subbasin_percent_2018_fig" src="https://github.com/user-attachments/assets/67cc02ef-cbd4-4378-85b6-4ce729ad5a1a" />
<img width="1200" alt="hyparea_subbasin_percent_2019_fig" src="https://github.com/user-attachments/assets/fdda604e-5199-4206-95ca-dd1b2100d1ee" />
<img width="1200" alt="hyparea_subbasin_percent_2020_fig" src="https://github.com/user-attachments/assets/4cd1f3a5-bfd2-4112-ab56-ee50dbee35e6" />




