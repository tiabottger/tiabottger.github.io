
## More profiles and linear drag
## More profiles
My previous velocity profiles averaged over the entire domain, using sigma layers. I was curious what the profiles looked like at specific points in the estuary, plotted versus depth in meters. I also plotted salinity profiles for comparison. The estuary is most stratified during neap tide on the 11-13th of the month as expected. This salinity stratification is strongest close to the river and decreases towards the ocean at the estuary mouth. The water column is pretty vertically mixed below 5 meter depth, but there is an interesting mid-water column velocity structure showing up that looks different from the bottom instrusion we would see in a salt wedge estuary. This is probably due to friction at the bed slowing flow and shifting the velocity peak upward. There is more vertical mixing as the estuary shallows shown in the salinity being lower.

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/de8383cb-a009-40f8-96b9-c34246a0ce58" />

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/431999b6-b599-43ae-b7e3-d4673f326b9a" />

On the ROMS Arakawa-C grid salinity and depth are stored on rho-points (middle points) while velocity is stored on u-points (edge points). To plot velocity versus depth, I used the nearest rho-grid depth to the u-grid point.

## Linear vs. quadratic drag
I created a new executable in which I modified the header file to define LDRAG instead of QDRAG and reran the model. The values for the drag coefficients are shown below, given in the BLANK.in file that becomes liveocean.in when make_dot_in.py is run as part of the LiveOcean wraparound code. The .in file is the ROMS input file. When LDRAG is defined, RDRG is used rather than RDRG2.
<img width="426" height="80" alt="image" src="https://github.com/user-attachments/assets/3df04a16-6234-4787-abee-92f8dd252961" />    

Below are profiles for the linear drag model run to provide comparison.
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/fb50612f-17ba-450d-8995-e63abc291ac6" />

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/a910204e-e288-4d50-b4b6-a51bd47d7aa7" />


Looking at the mouth, the quadratic drag profiles see more dampening in velocities toward the bed. Into shallower water the linear drag case is able to reach faster velocities especially apparent during neap tide. The difference between spring and neap tide (spring tide occuring the 3rd-7th, neap tide occurring the 11th-15th) is less pronounced in the linear drag case. In the quadratic velocity profiles, the structure is distinctly different, with a two-layer structure setting up during neap tide. Drag scales with u^2 in the quadratic case, which is more sensitive to stronger velocities during spring tide. In the linear drag case, the shape of the velocity profiles remains the same, with faster velocities during spring tide than neap tide. I suspect there is increased bottom stress during spring tide in the quadratic drag case which causes more mixing and creates the difference in profile shape. Interestingly, salinity stratification doesn't set-up during neap tide in the linear drag case. I think this is because at low velocities less than 0.1 m/s the linear drag coefficient is stronger than the quadratic drag coefficient, and strong enough to cause relatively large bottom stress even at low speeds.
