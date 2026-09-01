## Bottom DO SalishSeaCast LiveOcean comparison
We calculated the dissolved oxygen concentration in the bottom 14.6% of the water column for both SalishSeaCast and LiveOcean. This was the value corresponding to the bottom sigma layer of Salish Sea Model, such that we can compare the "bottom" values for all three models.

First, I plotted the time-averaged DO concentration over the year of 2014 as a spatial heatmap. Whidbey basin stands out as quite different between LiveOcean and SalishSeaCast. The DO concentrations for SalishSeaCast are fairly low throughout Whidbey basin, not just in terminal inlets such as Penn Cove. Surprisingly, Whidbey basin low DO concentrations seem to be comparable to Hood canal in SalishSeaCast. LiveOcean DO concentrations do not drop as low in Whidbey basin, although there are some lower values in Holmes harbor. The lowest DO values occurr in Lynch cove at the end of Hood canal, where it appears to be hypoxic (<= 2mg/L) on average. 
<img width="1000" src="https://github.com/user-attachments/assets/e53bbb7e-902e-41cd-8930-2dc3cee930e2" />

Next I plotted the hypoxic occurrence, comparing thresholds of 2 mg/L and 3 mg/L. Using a threshold of 2 mg/L, Hood canal doesn't light up for SalishSeaCast. I checked in with Tall about the very low hypoxic occurrence, and he said this is something the model has consistently represented in previous analyses. He has associated this behavior, at least partly, with a potential bathymetry issue in that region and says they are working on it. When the threshold is increased to 3 mg/L, Hood canal becomes more prominent in the SalishSeaCast result, along with "hotspots" in Whidbey basin. Interestingly, Penn cove doesn't seem to be an area of high hypoxic occurrence, rather, Port Susan, Holmes harbor, and the eastern part of Saratoga passage have the highest hypoxic occurrence. 

The plots for LiveOcean look more like what we have come to expect (although this expectation is largely based on LiveOcean model results). Hood canal has by far the most hypoxic occurrence, with hypoxia occurring most severely in Lynch cove. When we increase the threshold to 3 mg/L, the area of hypoxic occurrence expands throughout Hood canal, and we also see hypoxic days in Holmes harbor and a hint of color change in Penn cove suggesting some hypoxic days here as well.
<img width="1000" src="https://github.com/user-attachments/assets/8c6fe104-6e37-4e30-8012-6ddbd169d575" />

<img width="1000" src="https://github.com/user-attachments/assets/5e7d46cd-5c7f-4c9b-acfc-4df50f474534" />

I have consistently seen the largest disagreement between SalishSeaCast and LiveOcean model results occurring in Whidbey basin, but it is striking to see how different bottom DO in this region seems to be. The difference in information between the threshold set at 2 and 3 mg/L also is cause to consider what the limitations of the typical 2 mg/L threshold might be. In terms of how low DO effects species, we know that different species have different DO limitations. For example, Chinook salmon require more oxygen than this threshold, and Dungeness crabs have sufficient oxygen below the threshold in cold water, but not in warmer water when their metabolism increases.

### Hypoxic area and hypoxic volume
I calculated the hypoxic area for both models using the grid cell area, and the sum of cells in the bottom 14.6% layer that were <= 2 mg/L. I also calculated the hypoxic volume using the hypoxic thickness (thickness summing cells <= 2 mg/L) in addition to the sum of hypoxic cells in the bottom 14.6% layer. Note that the hypoxic thickness used the vertical resolution of each model, with the models having different vertical resolutions.

<img width="700" src="https://github.com/user-attachments/assets/f85392f6-f25f-48f1-962b-54f92ff4b772" />

<img width="700" src="https://github.com/user-attachments/assets/bc7a43ef-612f-4ac5-aeff-7989b5d5ba4e" />

For both the hypoxic area and volume, SalishSeaCast doesn't reach as high of a peak and drops off before LiveOcean values do. From previous results comparing models to observational data, we know that SalishSeaCast tends to be biased slightly lower than LiveOcean for dissolved oxygen values so this is consistent. I am curious about the difference in timing seen here, while hypoxic area and volume seem to increase at similar timing for both models, the decrease occurrs much sooner for SalishSeaCast.



