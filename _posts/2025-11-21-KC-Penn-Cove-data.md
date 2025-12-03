## KC Penn Cove data
This blog post is a place for notes taken while exploring existing biological data available in Penn Cove!

### Data available:
King County has two technical memos summarising monitoring:
- September 2023 - August 2024: [KC Year 2 summary](https://your.kingcounty.gov/dnrp/library/2024/kcr3593-2024/kcr3593-2024.pdf)
- February 2022 - August 2023: [KC Year 1 summary](https://your.kingcounty.gov/dnrp/library/2023/kcr3593/kcr3593.pdf)
This monitoring program was launched in response to Ecology releasing the Puget Sound Nutrient General Permit (PSNGP) June 2021. Ecology's Salish Sea Model (SSM) determined Whidbey Basin out of compliance DO compliance having a DO difference with/without anthroprogenic nutrient loading >0.2 mg/L, however a lack of empirical evidence in this area. This data set is intended for 1) validating SSM predictions, 2) improving SSM and other models, 3) understanding relative importance of nutrients, climate, local factors in deep water vs. shallow embayments.

Data collected:
- Profile casts (CT, DO, NO3, Chl, SA) processed into [LO/obs](https://github.com/parkermac/LO/tree/main/obs) codebase by Dakota. Bi-monthly.
- Bottles at surface, 5m, bottom for nutrient concentrations (nitrate + nitrite, ammonia, orthophosphate, silica). Bi-monthly. 
- Moorings (DO, N, Chl) 15 minute sampling frequency at surface and bottom.

### Some notes from reading KC memos and [KC long-term monitoring summary](https://green2.kingcounty.gov/sciencelibrary/Document.aspx?ArticleID=576) before diving into the Penn Cove Whidbey Basin data:
Whidbey Basin is more impacted by freshwater as compared to the Puget Sound's central basin with Skagit river inflows. As a result, phytoplankton blooms are different in their timing, magnitude, and composition here compared to the Central Basin: 
- Phytoplankton spring blooms occurred earlier as compared to Central Basin in 2022 (warmer temperatures/stronger stratification earlier?), February/March seem typical for start of the spring bloom with the exception of 2024 when spring bloom occurred in April and bloom was smaller.
- More phytoplankton biovolume in Whidbey Basin (most at Penn Cove, >150 mm^3/L during March spring bloom) as compared to Central Basin stations. More phytoplankton biomass explained by accumulation due to less flushing/ longer residence times or higher phytoplankton growth rates due to more favorable conditions (warmer temperature, more light access) or a combination? Data suggesting conditions are favorable for bloom formation earlier, and it can then persist longer.
- Penn Cove in Whidbey Basin especially had higher concentrations of *Noctiluca sp.* (not toxic but of concern due to potential release of ammonium), these are bioluminescent dinoflagellates. Puget Sound in general dominated by diatoms, with large-celled diatoms present year round, in Central Basin don't see a seasonal succession pattern that arises under nutrient limitation where other taxa (dinoflagellates that can swim) gain advantage over faster growing diatoms. Prolonged stratification leading to nutrient limiting conditions (varying vertically in water column) advantaging vertically migrating dinoflagellates over diatoms in Penn Cove --> harmful bloom events? (dinoflagellate bloom problem formers in Puget Sound include *Heterosigma*, *Cochlodinium*, *Karlodinuim*, *Akashiwo* which produce toxins. *Psuedo-nitschia*, one of the big HAB bulletin monitored species with neurotoxin accumulation in shellfish, are diatoms).

While we are thinking about nutrients in the Puget Sound in general as coming primarily from the ocean, in this system we have our eyes on the Skagit river and seasonal dynamics in discharge rates as comprising big part of nutrient loading signal-- I'm curious to explore this in the data! The Puget Sound is widely considered to be nitrate limited (the biogeochemistry of phosphorous changes as salinity increases, making phosphorous less limiting in marine systems as compared to freshwater), with surface dissolved nitrate concentrations decreasing to zero in the summer due to biological productivity. Red Alders have a symbiotic relationship with nitrogen fixing bacteria in their root tubules, providing the dissolved bio-available form in high concentrations in Washington rivers. 


## Questions
- Any work done with mooring time series data?    
- Plot something like this but with LO and Whidbey High-Res model comparison? <img width="700" alt="image" src="https://github.com/user-attachments/assets/b1de4e51-a56f-4f10-aee8-2c06498b9f4a" />

