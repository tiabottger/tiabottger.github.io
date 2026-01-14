## LO process summary for idealized runs
Leading into my own idealized model experiments, I found it important to return to the walkthrough for the grid `ae0` to understand where I can make changes to grid specifications and forcings. Here I summarize information I've learned about the key functions in this process for quick reference in the future. Next week I plan to add a section for creating a `dot_in` file for a ROMS run-- this allows you to adjust forcing, boundary counditions for different runs without remaking a grid.

-------------
References:
- https://github.com/parkermac/LO/blob/main/notes/analytical_runs.md
- https://github.com/parkermac/LO/tree/main/pgrid
- https://github.com/parkermac/LO_roms_user/blob/main/README.md
- https://ajleeson.github.io/research_blog/2022/06/26/idealized-estuary-process-flowchart.html
----------------- 
### Grid creation `LO/pgrid.py` 
**Purpose:**   
defines grid coordinates, bathymetry, boundaries, atmospheric nudging, masks, exclusions etc.
**Input:**  
calls in user specifications in **LO_user/pgrid/gfun_user.py**  
  -  **gridname**   
    <img width="1316" height="76" alt="image" src="https://github.com/user-attachments/assets/deb30063-7370-4656-bdc0-34f520238a90" />
  - **grid specifications** 
    <img width="1680" height="1120" alt="image" src="https://github.com/user-attachments/assets/f7df436d-0a1a-4afa-89c1-3f114ed769f4" />

**Output:**
- LO_data/grids/ae0
  - S_COORDINATE_INFO.csv
  - XY_COORDINATE_INFO.csv
  - dch.csv
  - river_info.csv
  - grid.nc
  - nudgecoef.nc
- LO_output/pgrid/ae0
  - choices.p
  - grid_m01_r01_s01_x01.nc this is created in a sequence of `start_grid`, `make_mask` (m), `carve_rivers` (r), `smooth_grid` (s), `make_extras` (x)
  - roms_river_info.csv
 
***Copy `LO_data/grids/ae0` to apogee and klone***

> *How are rivers defined?*  
> Non-analytical runs have files created which contain information about rivers (names, gage numbers) and their channel locations, which are created by LO/pre/river1 programs.
> For analytical cases, the river file and track is created by hand within gfun_user grid specifications:  
> <img width="950" height="574" alt="image" src="https://github.com/user-attachments/assets/b0112eff-0937-4066-a6b1-65761264bef8" />

-----------------
### Forcing file generation `LO/driver/driver_forcing00.py`
**Purpose:** 
define date range and forcings for grid, create forcing files in format that `driver_roms00.py` expects.   

***On apogee:***
<img width="1324" height="308" alt="image" src="https://github.com/user-attachments/assets/ab6cbcc4-d2b4-4775-ad00-804aa020186f" />


**Output:** 
- LO_output/forcing/ae0
  - f2020.01.01 forcing files in single day folders
---------------
## ROMS
### Compile 
When we compile ROMS, we need a `build_roms.sh` and `.h` header file for our executable. I copied the `xa0` executable folder from Parker's LO_roms_user (and push and pulled with github to apogee). These tell ROMS what parts of the code we want to interact with. So the \[ex] part of a run name tracks what version of ROMS was compiled. In the header file, we can define and undefine choices we want ROMS to run with e.g.:  
<img width="400" height="252" alt="image" src="https://github.com/user-attachments/assets/2c10abbc-54a5-4bf3-a489-5543750f128c" />

***On klone***
<img width="1794" height="456" alt="image" src="https://github.com/user-attachments/assets/0e022e42-0ffe-4642-8a68-eb62b74340c9" />

**Output:**
- LO/roms_user/\[ex]
  - bld.log (where command line output is written to, can check for progress while compiles)
  - Build_romsM

### Run `LO/driver/driver_roms00.py`

***On klone head node***
<img width="1904" height="192" alt="image" src="https://github.com/user-attachments/assets/7b8a48b2-1a52-4eeb-a7ad-df691ae05b55" />

**Output:**  
in *gtagx* form   
\[gridname]_\[tag]\_\[ex]




  
