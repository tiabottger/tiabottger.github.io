I modified the initial salinity gradient within the forcing file following LiveOcean wraparound code procedure, which led to some exploration of how LiveOcean intersects with ROMS. When we do a model run we run the script `LO/driver/driver_roms00.py`. This relies on `LO/driver/batch/klone00_batch_BLANK.sh`. This shell script ([here](https://github.com/parkermac/LO/blob/main/driver/batch/klone00_batch_BLANK.sh)) contains the actual command to run ROMS in line 36:
<img width="700" alt="image" src="https://github.com/user-attachments/assets/2ffdc2e3-f738-4dcb-9015-9c40b7679f53" />
  
This uses a liveocean.in input file, which is produced from BLANK.in in `LO_user/dot_in/[grid]_[tag]_[ex]`. The C-preprocessing name is of the executable, for example `MyAppCPP = XA0`. Parker has set up LiveOcean to change CPP parameters in the executable header file found in `LO_roms_user/[ex]` for example xa0 [here](https://github.com/parkermac/LO_roms_user/blob/main/xa0/xa0.h). This is where you turn on biology, for example how it is done in the current run using xllb [here](https://github.com/parkermac/LO_roms_user/blob/main/x11b/x11b.h).
<img width="500" alt="image" src="https://github.com/user-attachments/assets/f599aedb-f84b-44c2-af9c-adda966071a9" />

We could set the salinity initial condition directly here rather than in the forcing, when we compile ROMS it is using the choices definied in the executable header file. The liveocean.in file lives within `LO_roms\[grid]_[tag]_[ex]\fyyyy.mm.dd` which is the `roms_out_dir` where netcdf output files are also sent.

--------------------------

Working with model run output
https://github.com/parkermac/LO/blob/main/extract/lowpass/extract_lowpass.py
