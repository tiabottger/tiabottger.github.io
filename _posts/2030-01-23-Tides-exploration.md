
## Tides exploration
Now that I have created model output forced by tides only, I want to take a moment to learn about tides using results to facilitate my learning exploration!

### Tidal consituents
Tides are created by the gravitational pull from the moon and sun, whose relative effect changes in relation to Earth's orbit. There are many [harmonic tidal constituents](https://tidesandcurrents.noaa.gov/about_harmonic_constituents.html), the periodic motions of the Earth, sun, and moon, that have been identified which together describe the gravitational tug felt by tides at a given time and location. The amplitude of the gravitational force is based mass and the distance between these objects, with peaks when the distance shrinks. Standing in one place on the Earth, we see the sun and moon "setting" as they draw further away from us due to the spin of the Earth on its axis. The largest constituents are those we are most familiar with in our daily life:
- M2: the largest lunar constituent. The gravitational pull of the moon as the Earth spins on its axis. The period of M2 is 12.42 hours. The Earth rotates on its axis once every 24 hours, and in the time it takes to complete this orbit the moon has orbited 50 minutes on its monthly orbit path relative to the Earth's starting point. So Earth needs an additional 50 minutes to "catch-up" to the position closest to the moon. Hence M2 has two peaks every 24 hours and 50 minutes.
- S2: the largest solar constituent. The gravitational pull of the sun as the Earth spins on its axis. The period of M2 is 12 hours, the Earth is closest to the sun twice every 24 hours.

The difference between these two periods superimposed creates the two week [spring-neap tidal cycle](https://oceanservice.noaa.gov/facts/springtide.html) (half the moon's monthly orbit). When the moon and sun are lined up, during a full moon or new moon, the gravitational force of both perfectly add/subtract to create stronger tides known as spring tides. During a spring tide tides "spring forth" and there are the largest differences between ebb and flood and the strongest currents. When the sun and moon are 90 degrees from eachother, tides are more moderate and known as neap tides.

You can imagine other constituents adding complexity as Earth's orbit around the sun is elliptical, and it is moreover tilted on its axis. The next largest component is SA, solar annual with a period of a year or 365.25 days for Earth to complete an entire orbit. There are 37 harmonic constituents capturing the periodic nature of changing gravitational forces, all of these cosine curves adding up to the complex curve of highs and lows of tides predicted accurately far into the future. But on a shorter term we can simplify things and say tides have a period of about 12.42 hours, because their largest gravitational influence is the moon M2 component being closest to the Earth.
#### How do we form our tidal forcing?
Tidal forcing for the analytical case is created in the script 'forcing/tideA0/make_forcing_main'. This creates a spring neap tidal cycle by defining M2 and S2 periods and initial amplitudes of 0.75 and 0.25 for their relative contributions (M2 accounting for 75% of the tidal signal). The result forced over two weeks is as shown:

### Tides in the Puget Sound
While I'm looking at an idealized estuary, I want to bring everything I am learning back to the Puget Sound context. My idealized estuary removes the deep glacially carved constrictions and complexity of the Puget Sound's fjords, as if I took a knife and cut out a slice of Puget Sound pie. But make that a very shallow slice, because the mean depth of my estuary is about 10 m while the Puget Sound is about 140 m depth on average. The entrance into my estuary roughly maps to the Strait of Juan de Fuca (20 km across), and the extent of my estuary (100 km long) is about from Admiralty inlet to Tacoma. Less volume. Constrictions, sills are what makes things interesting in Puget Sound and I've removed these!! 
Bigger in Tacoma than whidbey, standing wave envelope
NOA tides


### Amplitude
plot of amplitude vs x 
maybe just along the gradual shallowing part?

### Phasing
relative to the wave speed, as the depth shallows wave slows down. peaks would take longer to pass the same point. phase shift increases.

plot of depth vs wave speed? 
lagged correlation for phase
