## LO process summary for idealized runs
Leading into my own idealized model experiments, I found it important to return to the walkthrough for the grid `ae0` to understand where I can make changes to grid specifications and forcings. Here I summarize information I've learned about the key functions in this process for quick reference in the future.

-------------
References:
- [https://github.com/parkermac/LO/blob/main/notes/analytical_runs.md](https://github.com/parkermac/LO/blob/main/notes/analytical_runs.md)
- [https://github.com/parkermac/LO/tree/main/pgrid](https://github.com/parkermac/LO/tree/main/pgrid)
- [https://github.com/parkermac/LO_roms_user/blob/main/README.md](https://github.com/parkermac/LO_roms_user/blob/main/README.md)
- [https://ajleeson.github.io/research_blog/2022/06/26/idealized-estuary-process-flowchart.html](https://ajleeson.github.io/research_blog/2022/06/26/idealized-estuary-process-flowchart.html)
  
----------------- 
### Grid creation `LO/pgrid.py` 
**Purpose:**   
defines grid coordinates, bathymetry, boundaries, atmospheric nudging, masks, exclusions etc.    
**Input:**   
calls in user specifications in **`LO_user/pgrid/gfun_user.py`**  
  -  **gridname**   
    <img width="1316" alt="image" src="https://github.com/user-attachments/assets/deb30063-7370-4656-bdc0-34f520238a90" />
  - **grid specifications** 
    <img width="1674" alt="image" src="https://github.com/user-attachments/assets/5b2b60ed-5273-48f0-92df-469c9f57aa44" />


***Commit/push changes to LO_user in GitHub***

- run series of commands in LO/pgrid (from iPython) to create grid files: `start_grid`, `make_mask`, `carve_rivers`, `smooth_grid`, `make_extras`, `grid_to_LO`

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
  - grid_m01_r01_s01_x01.nc *indexing indicating changes to: mask (m), river (r), smoothing (s), or extras (x)*
  - roms_river_info.csv
 
***Copy `LO_data/grids/[gridname]` to apogee and klone***

> **How are rivers defined?**  
> Non-analytical runs have files created which contain information about rivers (names, gage numbers) and their channel locations, which are created by LO/pre/river1 programs.
> For analytical cases, the river file and track is created by hand within gfun_user grid specifications:  
> <img width="950" alt="image" src="https://github.com/user-attachments/assets/b0112eff-0937-4066-a6b1-65761264bef8" />

---------------
### Forcing instructions for ROMS: `dot_in` files  
**Purpose:**
`dot_in` files tell ROMS how many input forcing files we are providing and where to find these input files. Within these you can specify how often to output history files and how to partition the model grid when running on a different number of cores. Call in forcing and boundary conditions without remaking the grid.

**`LO_user/dot_in/[gridname]_[tag]_[ex]`**
- update `forcing_list.csv` with forcing scripts for ocean, tides, river, atm etc. Adjust open boundary conditions to the directions open to the ocean.
  ```
  ocn,ocnA0
  riv,norivA0
  tide,tideA0
  open,NSW
  ```
- update `make_dot_in` with number of cores you plan to use on klone
- adjust output variables and file to accept relevant forcing in `BLANK.in`

***Commit/push changes to LO_user in GitHub***

----------------
### Forcing file generation `LO/driver/driver_forcing00.py`
**Purpose:** 
defines date range and points to forcings for grid, creates forcing files in format that `driver_roms00.py` expects.   

**Input:**   
calls in forcing scripts from **`LO/forcing/[FRC]/make_forcing_main.py`**   
- to modify forcing (eg. river flow rate) copy to LO_user and adjust scripts directly. For example in `LO_user/forcing/norivA0/make_forcing_main.py`:  
<img width="1506" alt="image" src="https://github.com/user-attachments/assets/c31ce83b-48e5-40aa-87ad-1e2973a61e1d" />

***Commit/push changes to LO_user in GitHub***

***On apogee:***   
***Pull LO_user changes***     
<img width="800" alt="image" src="https://github.com/user-attachments/assets/e79c57f5-ab19-4ebb-b760-b9fded15d18a" />

> **Note:** -s new for ocean start type sets up initial conditions

**Output:** 
- LO_output/forcing/ae0
  - f2020.01.01 forcing files in single day folders

---------------
## ROMS
### Compile 
**Purpose:**   
compiling ROMS converts to machine-readable code. We need a `build_roms.sh` and `.h` header file for our executable. These tell ROMS what parts of the code we want to interact with. So the \[ex] part of a run name tracks what version of ROMS was compiled. When we have a run with biogeochemistry turned on, we will additionally have a `Fennel.h` header file. In the header file, we can define and undefine choices we want ROMS to run with. 

- copy executable folder from Parker's [LO_roms_user](https://github.com/parkermac/LO_roms_user/blob/main/README.md).   
**`LO_roms_user/[ex]`**
- define and undefine choices in header file, for example in `LO_roms_user/xa0/xa0.h`:  
  <img width="400" alt="image" src="https://github.com/user-attachments/assets/2c10abbc-54a5-4bf3-a489-5543750f128c" />
     
***Commit/push changes to LO_roms_user in GitHub***
   
***On klone***    
***Pull LO_user, LO_roms_user changes***
<img width="1794" alt="image" src="https://github.com/user-attachments/assets/0e022e42-0ffe-4642-8a68-eb62b74340c9" />

aliases:
```
alias mli='module load intel/oneAPI'
alias compile='./build_roms.sh -j 10 < /dev/null > bld.log &'
```

**Output:**
- LO/roms_user/\[ex]
  - bld.log (where command line output is written to, can check for progress while compiles)
  - Build_romsM
    - this should be full of files! make sure wait until see a message like `ar: creating /gscratch/macc/tbottger/LO_roms_user/xa0/Build_romsM/libROMS.a`
  -RomsM
    - this is the actual executable, finished runnable program
> **Can run:** 
>`squeue -A macc -u tbottger` to check on job status

-----------
### Run `LO/driver/driver_roms00.py`
**Purpose:** 
 load forcing files from apogee, make the dot_in file for each day, make the sbatch script, run ROMS for each day, send the ROMS output to apogee
 
***On klone head node***
<img width="2120" alt="image" src="https://github.com/user-attachments/assets/8557f188-591a-4a1c-b8e9-9bf89cc913a9" />


- For the old "compute" nodes you would want to use -np as some integer times 40, e.g. 40, 80, 200. If you use 200 for example your job will be using 5 nodes, which you can confirm sith squeue.
- For the new cpu-g2 nodes you would want to use -np as some integer times 32, e.g. 32, 64, 160, 192. It can be more reliable to have a job on one node, so 192 is a good maximum value.

LO/dot_in/ae0_t0_xa0 has code to accomodate 64 cores.   
To run my no river version over 2 weeks on coenv cpu-g2 (faster than macc compute):
```
python3 driver_roms00.py -g ae0 -t tnoriv -x xa0 -s newcontinuation -0 2020.01.01 -1 2020.01.15 -grp coenv -cpu cpu-g2 -np 64 < /dev/null > ae.log &
```
To continue a run (extend for more dates) use flag -continuation.

**Output:**  
On klone:  
- LO_roms/\[gridname]_\[tag]\_\[ex]
  - f2020.01.01 output files in single day folders
    - if you don't see all the days here fear not! They have all been sent to apogee (assuming klone only stores a limited amount)

On apogee:   
- LO_roms/\[gridname]_\[tag]\_\[ex]
  - f2020.01.01 output files in single day folders

***Copy `LO_roms/\[gridname]_\[tag]\_\[ex] to computer to make plots, or run plotting scripts from apogee***   

can do this with a command like:  
`scp -r tbottger@apogee.ocean.washington.edu:/dat2/tbottger/LO_roms/ae0_t0_xa0 .` where the destination `.` is the current directory

