## 2014 property-property plots

<img width="800" alt="bottle_2014_all_shallow" src="https://github.com/user-attachments/assets/6264ea79-ecf8-4d06-bcac-fe21e797e6b7" />

Depths above 30 m

<img width="800" alt="bottle_2014_all_deep" src="https://github.com/user-attachments/assets/508fe18f-03eb-4050-90ed-84683cbe3550" />

Depths below 30 m

<img width="800" alt="bottle_2014_all" src="https://github.com/user-attachments/assets/c0acb2e7-1bb1-4263-9b03-28483cea40f4" />

All depths

## 2014 plots by basin
<img width="800" alt="bottle_2014_hc_all" src="https://github.com/user-attachments/assets/931b52d2-536f-483f-98c9-e5e9f3dfd875" />

Hood canal

<img width="800" alt="bottle_2014_wb_all" src="https://github.com/user-attachments/assets/f79d0ae6-8493-4072-8336-fec9f2cedb04" />

Whidbey basin

<img width="800" alt="bottle_2014_mb_all" src="https://github.com/user-attachments/assets/fe072261-7dc2-49ad-8512-89973ab34840" />

Main basin

<img width="800" alt="bottle_2014_ss_all" src="https://github.com/user-attachments/assets/8604a2ca-470c-4397-b2ff-d3fcae7a164b" />

South Sound

## Initial takeaways
- SalishSeaCast and LiveOcean dissolved oxygen values diverge with depth. SalishSeaCast predictions have similar bias regardless of depth, while LiveOcean predicts shallow values more closely than values at depth (bias -8.2 vs -16.3).
- LiveOcean DO levels have the least error in Whidbey Basin and Hood Canal (bias -12.0 and -15.1 as compared to -18.7 and -19.9) while SalishSeaCast DO levels have the least error in Main Basin and South Sound (bias -25.8 and -27.6 as compared to -31.9 and -33.3).
- NO3 has the least error in Main Basin for both models. SalishSeaCast NO3 has the highest error in Hood Canal, while LiveOcean NO3 has the highest error in South Sound. The same is true for DIN, the sum of NO3 and NH4. SalishSeaCast NH4 also has the least error in Main Basin and highest error in Hood Canal. LiveOcean NH4 has the least error in Whidbey Basin and highest error in South Sound. 

### Thinking about differences between basins...
- Hood canal has restricted exchange due to sill near entrance, deep water can remain isolated for a long time.
- Whidbey basin is strongly freshwater influenced, circulation more strongly driven by river discharge.
- Main basin closer to ocean inflow, connected through Admiralty inlet, more frequently renewed.
- South Sound is relatively shallow, separated from Main Basin by constrictions. 

### Differences between LiveOcean and SalishSeaCast biogeochemistry
LiveOcean uses an NPZD (dissolved inorganic nitrogen, phytoplankton, zooplankton, and detritus) nitrogen-based model. The nutrient pool includes all forms of dissolved inorganic nitrogen (nitrate, nitrite, ammonium etc.) Chlorophyll is estimated from phytoplankton biomass using a chlorophyll to nitrogen ratio. Biogeochemical processes are represented as transformations of different forms of nitrogen between these pools (Davis et al. 2014). 

SalishSeaCast also uses an NPZD-type model using the currency of nitrogen coupled with silicon cycling. This biological component is called SMELT: Salish Sea Model Ecosystem-Lower Trophic. The dissolved nutrients tracked are nitrate, ammonium, and silica. These are taken up by three phytoplankton groups: diatoms, flagellates, and *M. rubrum* a mixotrophic ciliate (Olson et al. 2020). SalishSeaCast tracks multiple phytoplankton groups while LiveOcean has one phytoplankton group. There are fewer interacting parameters in LiveOcean, however better process detail does not necessarily produce better predictive skill.     

<img width="500" height="336" alt="image" src="https://github.com/user-attachments/assets/205a171b-0738-468a-ab35-ead2b342be06" />          

SalishSeaCast biological component, from Olson et al. 2020

### Differences in model domain
LiveOcean model domain extends across the continental shelf with the open ocean boundary located far offshore, while SalishSeaCast has its western boundary at the entrance to the Strait of Juan de Fuca. As a result, LiveOcean resolves much of the transport pathway for water entering the Puget Sound, while for SalishSeaCast a larger fraction of the incoming ocean signal must be prescribed at the open boundary. The open boundary conditions on temperature and salinity in the Strait of Juan de Fuca are based on fields from LiveOcean rather than climatology (Olson et al. 2020).       

<img width="500" height="390" alt="image" src="https://github.com/user-attachments/assets/256733ba-3c87-4cc1-9b25-9a8bdbc9145b" />             

SalishSeaCast model domain, from Soontiens et al. 2016

### Different vertical coordinates
LiveOcean uses terrain following sigma coordinates while SalishSeaCast uses z-level coordinates. Terrain following coordinates can maintain high resolution near the bottom and surface, and may better represent bottom dynamics such as flow over sills because coordinate surfaces align with flow pathways while z-level coordinates represent bottom topography as a staircase.
