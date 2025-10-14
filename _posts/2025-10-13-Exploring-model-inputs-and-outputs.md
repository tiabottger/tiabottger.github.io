## Exploring model inputs and outputs

Working with large files! Before pulling any source code, I had to ensure that my ~/.gitconfig had the appropriate git-lfs configuration for correctly downloading some roms_test input and observation NetCDF files. Git LFS is a command line extension specifically for managing large files with Git.

arrays in NetCDF grid file: 
- `xl`: basin X-length
- `el`: basin Y-length
- `h`: bathymetry
  - The bathymetry for ROMS is measured positive downwards, from a datum such as mean sea level (MSL). For a 'typical' ROMS application, the bathymetry would consist of all positive values.
- masking follows ROMS convention of having 1 = water, 0 = land

Model grid and how variables are placed in it. 
Variables rho, psi, u, and v refer to where variables are located relative to a model grid cell. <img width="300" alt="image" src="https://github.com/user-attachments/assets/b1e3009e-c9a2-4122-b453-70c0e24df9bc" />
