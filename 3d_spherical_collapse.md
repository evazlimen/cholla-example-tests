# 3D Spherical Collapse
This test illustrates the ability of a code to handle gravitational collapse due to spherical overdensity. The test consists of a sphere of radius 0.2 centered at (0.5, 0.5, 0.5) with a density of 1, surrounded by a background density of 0.0005. Pressure is constant everywhere at 0.0005. This test is performed with the ??? build (`cholla/builds/make.type.??`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Spherical_Overdensity_3D()`. 

## Parameter file: (`cholla/examples/3D/Spherical_Collapse.txt`)
Note that the output directory needs to be changed for the user.
```
#
# Parameter File for the 3D Sphere Collapse.
#

######################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# output time
tout=0.38
# how often to output
outstep=0.01
# value of gamma
gamma=1.66666667
# name of initial conditions
init=Spherical_Overdensity_3D
# domain properties
xmin=0.0
ymin=0.0
zmin=0.0
xlen=1.0
ylen=1.0
zlen=1.0
# type of boundary conditions
xl_bcnd=1
xu_bcnd=1
yl_bcnd=1
yu_bcnd=1
zl_bcnd=1
zu_bcnd=1
# path to output directory
outdir=/data/groups/comp-astro/bruno/cosmo_sims/sphere_collapse/output_files/
#outdir=/raid/bruno/data/cosmo_sims/cholla_pm/sphere_collapse/
#outdir=/gpfs/alpine/scratch/bvilasen/ast149/sphere_collapse/output_files/
```
Upon completion, you should obtain 39 output files. The initial and final densities (in code units) of a slice along the y-midplane is shown below.  Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/spherical-collapse_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with circle of density 1 and radius  51.2 centered on (128,128). The remaining cells have a density of 0.0005. The rightmost plot is the final density plot at t = 0.38 with " width="1200" />  
A skewer in x along y and z midplanes yields the 1-dimensional solution (density and pressure):  
<img src="./images/spherical-collapse_density_x.png" alt="On top are two scatter plots side by side of density vs cells in the x direction. The leftmost is the initial density plot with a constant density 1 across cells 75-175 and a density of 0.0005 elsewhere. The rightmost plot is the final density plot at t = 0.38. On bottom there are two scatter plots side by side of pressure vs cells in the x direction. On the left is the inital pressure function, with a value of 0.0005. On the right is the final pressure function. " width="1200" />  
Currently (8/1/23) this test is producing identical initial and final states regardless of whether the default hydro or gravity build is used. 
