
## Salinity gradient estuary
I am setting myself up to explore results on the idealized `ae0` grid, but this time with an initial salinity gradient rather than the ocean forcing file being set to salinty=30 everywhere. To establish the salinity gradient I am using the example of the [Estuary Test Case](https://www.myroms.org/wiki/ESTUARY_TEST_CASE) from the ROMS source code. This has been set-up with the following initial salinity distribution:

<img width="500" alt="image" src="https://github.com/user-attachments/assets/64b2df72-81ed-4472-9df0-a5708340cf69" />

My goal for this week is to find where the initial condition is specified and to impose the same salinity gradient onto my idealized estuary, confirming the set-up by replicating the above plot for my run.

The initial conditions are set in the ocean forcing python executable. For example for the `ocnA0` executable, salinity=30 everywhere is set in line 65 [here](https://github.com/parkermac/LO/blob/main/forcing/ocnA0/make_forcing_main.py): 
<img width="500" alt="image" src="https://github.com/user-attachments/assets/99265508-90a3-48b2-bb55-90ae9cb5a460" />

The ocean forcing executable is LiveOcean code that "wraps around" ROMS. The files 'ocean_clm.nc', 'ocean_ini.nc', and 'ocean_bry.nc' get written into by the python executable. These are the files that ROMS uses for model boundary and initial condition states. 

The header file `estuary.h` tells ROMS what specifications are active when compiling. It defines ANA_INITIAL which reads from ana.initial.h. Looking into this file I found the following block of code defining the initial salinity gradient [here](https://github.com/myroms/roms/blob/develop/ROMS/Functionals/ana_initial.h):
<img width="500" alt="image" src="https://github.com/user-attachments/assets/f722100d-47b1-4533-b0bd-da8375c3896a" />



