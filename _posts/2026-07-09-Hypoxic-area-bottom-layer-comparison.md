## Hypoxic area bottom layer comparison

Using the weighted average method described in my previous blogpost, I calculated the bottom DO concentration corresponding to the bottom sigma layer of Salish Sea Model (the bottom 14.6% of the water column) which uses a resolution of 10 sigma layers as compared to LiveOcean's 30. I defined the bottom 14.6% of the water column based on the bathymetry depth. 

Below I've plotted the hypoxic area as calculated using the concentration in the bottom cell of LiveOcean as compared to the bottom 14.6% of the water column layer. The hypoxic area calculation using the bottom 14.6% layer returns less hypoxia than the bottom cell calculation. This makes sense, the bottom 14.6% layer is averaging the concentration over a larger portion of the water column, which "dilutes" the concentration leading to less values falling below the 2 mg/L threshold. 

<img width="3300" alt="image" src="https://github.com/user-attachments/assets/749e335a-313b-4fc4-908d-0bc8bff5fdb2" />

I subtracted the thickness of the bottom LiveOcean cell from the thickness of the bottom 14.6% of the water column layer to identify where the difference is greatest. In deep areas, the bottom 14.6% of the water column layer is upwards of 30-35 m thicker than the bottom layer created by LiveOcean's 30 sigma layers. In shallow areas there is little difference because the water column is resolved well by fewer sigma layers. 

<img width="500" alt="bottom_layer_thickness_difference" src="https://github.com/user-attachments/assets/7c654000-53af-40ec-ad6b-5e5ab7088872" />
