## Profiles from salinity gradient estuary
I modified the initial salinity gradient within the forcing file following LiveOcean wraparound code procedure, which led to some exploration of how LiveOcean intersects with ROMS. When we do a model run we run the script `LO/driver/driver_roms00.py`. This relies on `LO/driver/batch/klone00_batch_BLANK.sh`. This shell script ([here](https://github.com/parkermac/LO/blob/main/driver/batch/klone00_batch_BLANK.sh)) contains the actual command to run ROMS in line 36:
<img width="700" alt="image" src="https://github.com/user-attachments/assets/2ffdc2e3-f738-4dcb-9015-9c40b7679f53" />
  
This uses a liveocean.in input file, which is produced from BLANK.in in `LO_user/dot_in/[grid]_[tag]_[ex]`. The C-preprocessing name is of the executable, for example `MyAppCPP = XA0`. Parker has set up LiveOcean to change CPP parameters in the executable header file found in `LO_roms_user/[ex]` for example xa0 [here](https://github.com/parkermac/LO_roms_user/blob/main/xa0/xa0.h). This is where you turn on biology, for example how it is done in the current long hindcast using xllb [here](https://github.com/parkermac/LO_roms_user/blob/main/x11b/x11b.h).    
<img width="500" alt="image" src="https://github.com/user-attachments/assets/f599aedb-f84b-44c2-af9c-adda966071a9" />

We could set the salinity initial condition directly here rather than in the forcing, when we compile ROMS it is using the choices definied in the executable header file. The liveocean.in file lives within `LO_roms\[grid]_[tag]_[ex]\fyyyy.mm.dd` which is the `roms_out_dir` where netcdf output files are also sent.

--------------------------
### Model output
Plotting the water level tidal forcing alongside the estaury salinity, it appears that two-layered estuarine flow initially appears, but spring tide mixes the two layer structure and it isn't able to set up again until neap tide around the 12th of the month.
<p style="text-align:center;"><video src="https://github.com/user-attachments/assets/ac2d7e49-a6d0-4c8e-a005-b563cdd99820" controls="controls" style="max-width: 800px;"></video>      

I plotted subtidally averaged velocity profiles to explore this further. Model output was averaged over 24 hours. Indeed, there is the greatest difference in surface vs. bottom velocity during neap tide on the 11-13th. 

<img width="500" alt="ae0_velocityprofiles" src="https://github.com/user-attachments/assets/9bc6d569-83d6-4761-bd45-5b63c476a08b" />      
     
Here, the velocity profile is plotted versus s_rho. LiveOcean and ROMS use the terrain-following sigma coordinate with 30 layers. s=0 is defined as the surface and s=-1 is the bottom. The depth in meters depends on the local bathymetry. To convert to meters, there is a tool in `zrfun.py` which is a function of bathymetry h, sea surface height zeta, and S. However, for a physically meaningful profile vs. depth I would need to first convert to depth coordinates before averaging horizontally rather than converting after averaging. 

