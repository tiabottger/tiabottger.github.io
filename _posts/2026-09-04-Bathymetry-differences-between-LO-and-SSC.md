## Bathymetry differences between LiveOcean and SalishSeaCast

<img width="1500" src="https://github.com/user-attachments/assets/d995345f-7804-4c43-93f6-be058f33a748" />

The total volume of the Puget Sound (within the basin mask) in LiveOcean is **168.33 km3** compared to a total volume in SalishSeaCast of **126.52 km3**. There are a couple of regions included in the LiveOcean grid that are not on the SalishSeaCast grid. These are the flats and river deltas coming into Whidbey basin which SalishSeaCast doesn't include in its grid. Agate passage above Bainbridge island is not connected on SalishSeaCast's grid. There also isn't connectivity between Indian island close to the entrance to the Puget Sound in SalishSeaCast. Several river bathymetries aren't included, however I believe freshwater inputs from them are.

To compare the bathymetry between the two models I mapped the bathymetry of SalishSeaCast onto the LiveOcean grid using a nearest-neighbor mapping approach. This allowed me to subtract the bathymetry of SalishSeaCast directly from LiveOcean.
Positive values (red): LiveOcean is deeper than SalishSeaCast. Negative values (blue): SalishSeaCast is deeper than LiveOcean.
<img width="600" src="https://github.com/user-attachments/assets/a63b4668-d6a0-4a9d-8a14-f56bde204a49" />

Whidbey Basin doesn't have a striking bathymetry difference between the two models, although what isn't apparent in this plot are the values in the Skagit flats and mud flats of Port Susan which are not included in SalishSeaCast's bathymetry. The biggest bathymetry differences between the models seems to be along the boundaries of Puget Sound. Also looking at each model's bathymetry side by side, It seems that SalishSeaCast has shallower shores which drop off to deeper depths more suddenly. This is causing the effect in the difference plot where the Puget Sound seems to be ringed in red: these values along the shore that are deeper in LiveOcean than in SalishSeaCast. Just inside the ring of red, SalishSeaCast has deeper values, where LiveOcean's bathymetry is more "smoothed" as it deepens along the shorelines. SalishSeaCast appears to be slightly deeper within main basin. 

---------

A big reason to look into bathymetry differences between the two models is that we are comparing bottom DO concentrations in the lower 14.6% of the water column-- a layer that would include different parts of the water column depending on the depth of the total water column.

I looked at hypoxic area calculated using the bottom cell as compared to the bottom 14.6% of the water column. As we had seen for LiveOcean, the values in the bottom 14.6% layer are slightly "diluted" where the bottom 14.6% layer included a larger share of the water column than the bottom cell alone.

<img width="700" src="https://github.com/user-attachments/assets/ac9a0070-12d0-474c-bcfe-c8ad3755a674" />

<img width="700" src="https://github.com/user-attachments/assets/6f6f4ae5-76c5-4974-8abb-858d92abf7d1" />


