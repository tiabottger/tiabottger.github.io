## Tidal forcing mini experiment
My goals for this mini experiment are to understand the effect of changing bathymetry to tides propogating into an estuary. 

## Model set-up
`ae0` has atmospheric forcing set to zero and biology turned off. 
### Idealized estuary grid
The creation of the grid used `gfu.stretched_grid()` which creates high resolution (small grid spacing) in the central region of the grid and low resolution (larger grid spacing) towards the edges so as to not "waste" points outside the region of focus. The idealized estuary is centered at a latitude of 45 deg and longitude of 0 deg, with a river track at 45 degrees. For our grid, the resolution was defined to 500 m cells around the estuary area of focus (longitude 0 to 1, latitude 44.9 to 45.1) and 2500 m otherwise. 

We have an estuary that is 100 km long, with a mouth that is 20 km across. Along estuary, the depth shallows at a rate of $\frac{dz}{dx} = \frac{20}{100,000} = 0.0002$. This would give a depth of 0 at 100km, however the last quarter of the estuary (at x = 75 km) has been set to a constant depth of 5 m. 
> Note: the function `zfun.112xy` defined in `lo_tools` allows easy conversion between lat lon coordinates and meters given a reference (typically the middle of the grid). 

### Some theory thought exercises
A simple formula can be used to determine resonant period given a depth and wavelength in a system:  
$T = \frac{4L}{\sqrt{gh}}$  
in which L is estuary length and h is the mean depth of the estuary. For a mean depth of about 10 m, this would give an estuary with a resonant period of about 1.11 hours. If tidal forcing were to match this period, we would expect resonance for this estuary and runaway tidal amplitudes. Those would be really quick tides (a tidal period is around 12.42 hours), so our estuary is in the clear-- we won't see amplitudes getting away from us!

