## Getting set-up for an analytical ROMS run
### What I've learned about ROMS
LiveOcean uses the ROMS (Regional Ocean Modeling System), a numerical modeling scheme which solves the equations of motion for the ocean over variable bathymetry. You can explore the ForTran code directly on [GitHub](https://github.com/myroms/roms). ROMS has an active user community and the [Ocean Modeling Discussion Forum](https://www.myroms.org/forum/index.php) is a fun resource to see how other people are using ROMS, getting stuck, and debugging. The [WikiROMS](https://www.myroms.org/wiki/Documentation_Portal) is a great go-to for a deeper dive into the governing equations, coordinate system, etc. A couple things of note:
- The horizontal coordinate system uses orthogonal curvilinear coordinates (to account for the earth being a globe, coordinate lines are "curved" to intersect at right angles).
- The vertical coordinate system is stretched to follow over the terrain. 
- The model is "free-surface", meaning the surface elevation evolves in time capturing processes that would be lost in a rigid assumption, like tides. The ocean has many scales of waves propogating at the same time, with fast external/surface motions and slower internal modes-- for instance fast surface gravity waves we see breaking on the coasts vs. below the surface where the warm layer is moving relative to colder denser water (thermocline oscillations). To resolve this, ROMS uses a split time-stepping scheme that separates solutions of *barotropic* (fast, depth-averaged where entire wave propogates at same speed) and *baroclinic* (slow, deviation from depth-averaged flow) waves.

LiveOcean Python code "wraps-around" ROMS code, so I won't be interacting with it directly but it's useful to understand what's happening under the hood. Next week I plan to look through the default ROMS test case of [Wind-Driven Upwelling/Downwelling over a Periodic Channel](https://www.myroms.org/wiki/UPWELLING_CASE).

---

### First try using LiveOcean (LO) Code to generate forcing files
Following the steps in: [Analytical (idealized) ROMS simulations](https://github.com/parkermac/LO/blob/main/notes/analytical_runs.md) Christie, Maia and I met up and succeeded in making a grid of an idealized estuary + coast domain. This is `gridname = 'ae0'` in `LO_user/pgrid/gfun_user.py`. When you go into `LO/pgrid` and run the sequence of python commands, the code looks into my specific `LO_user` folder to grab the `gfun_user` file. Hence, LO code is run from within the LO directory, but I modify input scenarios and specifications from my own LO_user repo. This is an example of a "hook" built into the LO code! Here is what it looks like to run the first command `start_grid`:
<img width="900" alt="image" src="https://github.com/user-attachments/assets/6d5ea60e-532b-4e88-8f80-b567429d75e7"/>   
*Fig 1: Executing start_grid in LO/pgrid code imports my own gfun_user from LO_user*

The idealized domain created looks like this:  
<img width="500" alt="image" src="https://github.com/user-attachments/assets/0e4f9f8a-4c59-4df8-b64c-3a83afb2e08b" />   
*Fig 2: Idealized estuary domain. The color bar represents elevation, note we adjusted the zmin and zmax scale to match the example.*

We copied the output data generated in `LO_data/grids/ae0` to the remote apogee machine to create the forcing NetCDF files that ROMS will need to run. The reason for running them on apogee is that klone (the UW hyak supercomputer that has the computational resources needed to simulate a run) communicates with the remote machine, not my PC. NetCDF files contain multidimensional data, and I plan to explore these using the python `xarray` library before trying my first ROMS run on klone next week!
