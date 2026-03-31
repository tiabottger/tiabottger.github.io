## LiveOcean Hypoxic area and volume comparison figures

As part of the intermodel comparison discussion we would like to take a closer look at the hypoxic area and volume by subinlets in the Puget Sound. This is motivated by the question of where and when the most hypoxia occurs, and what differences there may be between LiveOcean and Salish Sea Model.

Aurora has created a script to run a timeseries of hypoxic volume from 2014-2020. This reads in a [box extraction](https://github.com/parkermac/LO/tree/main/extract/box) (using `LO/extract/box`) that effectively crops the raw LiveOcean output to a smaller domain to make these (still rather large) files easier to work with. Aurora has also further processed the files into netCDFs that contain time-variable bottom DO concentration, thickness of the water column, and thickness of the water column that is <= 2 mg/L, <= 1 mg/L and <= 3 mg/L. I used Aurora's [scripts](https://github.com/ajleeson/LO_user/tree/main/hypvol_for_intrmdl_cmprsn) as a jumping off point.

The following plots are a timeseries of the hypoxic volume and hypoxic area (the bottom grid cell area for cells <= 2mg) from 2014-2020.

<img width="1200" height="500" alt="hypvol_subbasin_comparison_fig" src="https://github.com/user-attachments/assets/aa69ba8f-ffea-4458-a402-64e91944b53f" />   
Fig 1. Hypoxic volume by subbasin timeseries

<img width="1200" height="500" alt="hyparea_subbasin_comparison_fig" src="https://github.com/user-attachments/assets/3690bbfb-e183-46c8-ae9f-3a79b8066dfb" />
Fig 2. Hypoxic area by subbasin timeseries

-------------------------
    
Similarly to the Salish Sea model, Hood Canal accounts for far and away the largest extent of hypoxia. Breaking this down by year, I also summed the total hypoxic area by subbasin as a percent of total hypoxic area for the entire Puget Sound.

<img width="1200" height="500" alt="hyparea_subbasin_percent_2015_fig" src="https://github.com/user-attachments/assets/f3fe065b-8766-4a77-94da-9f16b0e9f8d2" />
<img width="1200" height="500" alt="hyparea_subbasin_percent_2016_fig" src="https://github.com/user-attachments/assets/81daaed1-b3db-44fe-abb3-44a869c17ae1" />
<img width="1200" height="500" alt="hyparea_subbasin_percent_2017_fig" src="https://github.com/user-attachments/assets/1cbb1658-3860-45de-a0a1-082c73f2d953" />
<img width="1200" height="500" alt="hyparea_subbasin_percent_2018_fig" src="https://github.com/user-attachments/assets/53e36eb6-9217-4670-837b-1386e7761f28" />
<img width="1200" height="500" alt="hyparea_subbasin_percent_2019_fig" src="https://github.com/user-attachments/assets/52b4e941-8c6e-48dd-ae70-ce4de09349b8" />
<img width="1200" height="500" alt="hyparea_subbasin_percent_2020_fig" src="https://github.com/user-attachments/assets/3bc699b5-24ea-452d-808c-f1f2379f6b97" />
