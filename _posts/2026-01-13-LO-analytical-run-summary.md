Before designing my own analytical model experiments, returning to the analytical run walkthrough and summarizing information I've learned for quick reference in the future. 
Example here is from ae0 grid

References:
- https://github.com/parkermac/LO/blob/main/notes/analytical_runs.md
- 
- https://ajleeson.github.io/research_blog/2022/06/26/idealized-estuary-process-flowchart.html

### Grid creation
LO/**pgrid.py**

Purpose: defines grid coordinates 

boundary information, atmospheric nudging, masks, exclusions river info
Input
-   calls in user specifications in `LO_user/pgrid/gfun_user.py`
  -  **gridname**   
    <img width="1316" height="76" alt="image" src="https://github.com/user-attachments/assets/deb30063-7370-4656-bdc0-34f520238a90" />
    `dch`
  - **edit definition in elif gridname == 'ae0'** 
    where boundary conditions and river outputs for grid are specified.  

Output:
- `LO_data/grids/ae0`
  - `S_COORDINATE_INFO.csv`
  - `XY_COORDINATE_INFO.csv`
  - `dch.csv`
  - `river_info.csv`
  - `grid.nc`
  - `nudgecoef.nc`

- `LO_output/pgrid`
  - 

*How are rivers defined?*


### Forcing
LO/driver/**driver_forcing00.py**


### ROMS
**function:** `LO/driver/driver_roms00.py`

  
