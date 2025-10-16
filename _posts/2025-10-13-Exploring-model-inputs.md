## Exploring model inputs

Last week I used the LiveOcean collection of programs called `pgrid` to create an idealized estuary model grid and the NetCDF forcing files that are read into ROMS to run a simulation. Before my first run, I took a closer look at what was generated and what variables ROMS expects to find in a grid file. I glanced into `ROMS/Utility/get_grid.F`[here on Github](https://github.com/myroms/roms/blob/develop/ROMS/Utility/get_grid.F) to see what ROMS looks for in a grid in order to run. 

Christie also pointed me to `ROMS/External/varinfo.yaml`[here on GitHub](https://github.com/myroms/roms/blob/develop/ROMS/External/varinfo.yaml), the NetCDF Metadata dictionary! A master mega long list where all variables go to be defined! This will be useful for debugging, and I can use it as a starting place to find variables I might want to track through the code to see where they are occuring and what's happening to them. A trick is to use `grep` to find occurances of a variable, ex: `grep omega *.F` finds all occurances of the variable omega in the Fortran source files (`*.F`).

Some variable names/definitions I made note of for now:
- `xl`: basin X-length
- `el`: basin Y-length
- `h`: bathymetry
  - The bathymetry for ROMS is measured positive downwards, from a datum such as mean sea level (MSL). For a 'typical' ROMS application, the bathymetry would consist of all positive values.
- `mask_rho`, `mask_psi`, `mask_u`, `mask_v`: masking follows ROMS convention of having 1 = water, 0 = land.
- `f`: Coriolis parameter
- `pm`: coordinate transfomation scale factor (m) associated with the differential distances in xi
- `pn`: coordinate transfomation scale factor (n) associated with the differential distances in eta
- `spherical`: logical switch for spherical grid configuration. 

Many variables were defined seperately at rho, psi, u, and v points. These refer to where variables are located relative to a model grid cell:   
<img width="300" alt="image" src="https://github.com/user-attachments/assets/b1e3009e-c9a2-4122-b453-70c0e24df9bc" />  
*Fig 1. Rho, psi, u, and v points as shown in [ROMS wiki](https://www.myroms.org/wiki/Grid_Generation)*

Because the coordinate system is curvilear, new coordinates xi $\xi(x,y)$ and eta $\eta(x,y)$ have been defined. Scale factors defined in the grid as pm $m(\xi,\eta)$ and pn $n(\xi,\eta)$ relate the differential distances ($\Delta\xi, \Delta\eta$) to the actual physical distances.

Looking more closely at the idealized estuary grid I generated using the Python `xarray` library for reading NetCDF files, I can see how variables are defined spatially at each rho, psi, u, and v point on the xi eta coordinate grid. These are the "dimensions" of each variable. Note each time you run a piece of code in `pgrid` it makes a new grid file with the name altered to indicate what happened. The names start as: `grid_m00_r00_s00_x00.nc` with the letters and numbers indicating changes to: mask (m), river (r), smoothing (s), or extras (x). So the final grid is `grid_m01_r01_s01_x01.nc`. These are all stored in `LO_output/pgrid/ae0` while the final grid gets sent to `LO_data/grids/ae0` as `grid.nc` alongside other important info needed in the next step: 

<img width="500"  alt="image" src="https://github.com/user-attachments/assets/45550c98-abcf-4d96-a840-0186a22c6de7" />

*Fig 2. The contents of `LO_data/grids/ae0`, everything needed to create forcing files.*

```
<xarray.Dataset> Size: 17MB
Dimensions:    (eta_rho: 386, xi_rho: 348, eta_u: 386, xi_u: 347, eta_v: 385, xi_v: 348, eta_psi: 385, xi_psi: 347)
Dimensions without coordinates: eta_rho, xi_rho, eta_u, xi_u, eta_v, xi_v, eta_psi, xi_psi
Data variables:
    h          (eta_rho, xi_rho) float64 1MB ...
    pm         (eta_rho, xi_rho) float64 1MB ...
    pn         (eta_rho, xi_rho) float64 1MB ...
    f          (eta_rho, xi_rho) float64 1MB ...
    xl         float64 8B ...
    el         float64 8B ...
    spherical  <U1 4B ...
    lon_rho    (eta_rho, xi_rho) float64 1MB ...
    lat_rho    (eta_rho, xi_rho) float64 1MB ...
    mask_rho   (eta_rho, xi_rho) float64 1MB ...
    lon_u      (eta_u, xi_u) float64 1MB ...
    lat_u      (eta_u, xi_u) float64 1MB ...
    mask_u     (eta_u, xi_u) float64 1MB ...
    lon_v      (eta_v, xi_v) float64 1MB ...
    lat_v      (eta_v, xi_v) float64 1MB ...
    mask_v     (eta_v, xi_v) float64 1MB ...
    lon_psi    (eta_psi, xi_psi) float64 1MB ...
    lat_psi    (eta_psi, xi_psi) float64 1MB ...
    mask_psi   (eta_psi, xi_psi) float64 1MB ...
```

I've run into a but of a hangup in getting to my next goal of... 
### Exploring model outputs (stuck, no outputs!)
- To run ROMS on klone, I need to compile (done using `.build_roms.sh`). This is looking for `netcdf-ifort` and `netcdf-icc`, netCDF compilers in Intel Fortran and Intel C, which are in Parker's `gscratch/macc` that I don't yet have access to. Christie and I tried pointing to other modules on klone where the code could find these (using `module avail`) but we ran into an error with the version match-up and didn't want to get too far down this rabbit hole. I've set my directories in klone's .bashrc back to Parker's default so **I should be good to go once I get access**:
```
LODIR=/gscratch/macc/local
NFDIR=${LODIR}/netcdf-ifort
NCDIR=${LODIR}/netcdf-icc
export LD_LIBRARY_PATH=${NFDIR}/lib:${NCDIR}/lib:${LD_LIBRARY_PATH}
export PATH=/gscratch/macc/local/netcdf-ifort/bin:$PATH
export PATH=/gscratch/macc/local/netcdf-icc/bin:$PATH
```
- Looking into `LO_output/forcing/ae0` where I expected NetCDF forcing files generated from my ae0 grid to to be, I found the folders `f2020.01.01` and `f2020.01.02` for two days containing `ocnA0`, `rivA0`, and `tideA0`, **but no NetCDFs** (the `Data` folders within these were empty). When I ran the following commands:
```
python driver_forcing00.py -g ae0 -0 2020.01.01 -1 2020.01.02 -f rivA0
python driver_forcing00.py -g ae0 -0 2020.01.01 -1 2020.01.02 -f ocnA0 -s new
python driver_forcing00.py -g ae0 -0 2020.01.01 -1 2020.01.02 -f tideA0
``` 
out of `LO/driver` I had gotten the following error:
<img width="900" alt="image" src="https://github.com/user-attachments/assets/5ef5a01e-8c76-4989-8074-5608dac4d975" />
This printout comes from the following code at the bottom of `driver_forcing00.py`: <img width="500" height="470" alt="image" src="https://github.com/user-attachments/assets/ddaee2fd-292f-4235-847d-d98ad46be050" />  
Which seemed like it hadn't interfered with generating the forcing files (so we'd tried commenting out this for loop) but maybe needs further investigation.
