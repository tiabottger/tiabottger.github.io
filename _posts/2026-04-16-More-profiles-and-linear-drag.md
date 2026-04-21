
## More profiles
My previous velocity profiles averaged over the entire domain, using sigma layers. I was curious what the profiles looked like at specific points in the estuary, plotted versus depth in meters. I also plotted salinity profiles for comparison. The estuary is most stratified during neap tide on the 11-13th of the month as expected. This salinity stratificaiton is strongest close to the river and decreases towards the ocean at the estuary mouth. The water column is pretty vertically mixed below 5 meter depth, but there is an interesting mid-water column velocity structure showing up that looks different from the bottom instrusion we would see in a salt wedge estuary. This is probably due to friction at the bed slowing flow and shifting the velocity peak upward. There is more vertical mixing as the estuary shallows shown in the salinity being lower.

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/de8383cb-a009-40f8-96b9-c34246a0ce58" />

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/431999b6-b599-43ae-b7e3-d4673f326b9a" />

On the ROMS Arakawa-C grid salinity and depth are stored on rho-points (middle points) while velocity is stored on u-points (edge points). To plot velocity versus depth, I used the nearest rho-grid depth to the u-grid point.

## Linear vs. Quadratic drag
I created a new executable in which I modified the header file to define LDRAG instead of QDRAG and reran the model. The values for the drag coefficients are shown below, given in the BLANK.in file that becomes liveocean.in when make_dot_in.py is run as part of the LiveOcean wraparound code. The .in file is the ROMS input file. When LDRAG is defined, RDRG is used rather than RDRG2.
<img width="426" height="80" alt="image" src="https://github.com/user-attachments/assets/3df04a16-6234-4787-abee-92f8dd252961" />    

Below are profiles for the linear drag model run to provide comparison.
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/fb50612f-17ba-450d-8995-e63abc291ac6" />

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/a910204e-e288-4d50-b4b6-a51bd47d7aa7" />


Quadratic drag at the mouth sees more dampening in velocities toward the bed. Into shallower water the linear drag case is able to reach faster velocities especially apparent during neap tide. The difference between spring and neap tide (spring tide occuring Whether it is spring or neap tide seems to have less of an effect in the linear drag case, whereas there is a clear seperation between spring and neap tide for quadratic drag where differences in tidal velocities are more significant as drag scales with u^2. in which stratification is of a similar scale
