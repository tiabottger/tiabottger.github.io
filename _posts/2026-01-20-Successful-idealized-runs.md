## Successful idealized runs!  
My goal for my first idealized estuary mini experiment was to investigate how tides propogate into an estuary as bathymetry shallows. In practicing setting up for a run, I also ran the "default" version with river forcing, which will provide a nice comparison point.

I successfully ran two versions of forcing on the `ae0` idealized estuary grid, one with and one without river input: 
| Forcing | t0 | tnoriv |
| --- | --- | --- |
| **River** | flow rate = 1000 m3 s-1 | **flow rate = 0 m3 s-1**|
|       | salinity = 0 | same...
|       | temp = 10
| **Ocean** at t=0| salinity = 30 everywhere (including in estuary)
|       | temp = 10 
| **Tides** | period = 12.42 hrs 

Atmospheric forcing and biology are turned off.   
I ran this over 2 weeks: from 2020.01.01 to 2020.01.15.

### Idealized estuary grid
The creation of the grid used `gfu.stretched_grid()` which creates high resolution (small grid spacing) in the central region of the grid and low resolution (larger grid spacing) towards the edges so as to not "waste" points outside the region of focus. The idealized estuary is centered at a latitude of 45 deg and longitude of 0 deg, with a river track at 45 degrees. For our grid, the resolution was defined to 500 m cells around the estuary area of focus (longitude 0 to 1, latitude 44.9 to 45.1) and 2500 m otherwise. 
<img src="path/to/your/image.png" alt="Alt text" width="400" height="200">

We have an estuary that is 100 km long, with a mouth that is 20 km across. Along estuary, the depth shallows at a rate of $\frac{dz}{dx} = \frac{20}{100,000} = 0.0002$. This would give a depth of 0 at 100km, however the last quarter of the estuary (at x = 75 km) has been set to a constant depth of 5 m. 


### Some theory and thoughts
A simple formula can be used to determine resonant period given a depth and wavelength in a system:  
$T = \frac{4L}{\sqrt{gh}}$  
in which L is estuary length and h is the mean depth of the estuary. For a mean depth of about 10 m, this would give an estuary with a resonant period of about 1.11 hours. If tidal forcing were to match this period, we would expect resonance for this estuary and runaway tidal amplitudes. Those would be really quick tides (a tidal period is around 12.42 hours), so our estuary is in the clear-- we won't see amplitudes getting away from us!

## Future work 
