# 3D Uniform Grid
This example produces a uniform grid with zero density. This test is performed with the default hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Uniform_Grid()`.

## Parameter file: (`cholla/examples/3D/Uniform.txt`)
Note that the output directory will need to be modified according to the user.
```
#
# Parameter File for the 3D Uniform Grid.
#

######################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# output time
tout=0.0
# how often to output
outstep=0.01
# value of gamma
gamma=1.66666667
# name of initial conditions
init=Uniform
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
outdir=/raid/bruno/data/cosmo_sims/cholla_pm/uniform/
```
Upon completion, you should obtain 1 output file. The density (in code units) of a slice along the y-midplane is shown below. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/uniform_density_xz.png" alt="A 2D histogram showing density of cells in the z direction vs cells in x direction. Density is zero throughout the plot." width="1200" />  
Our grid is initialized uniformly with zero density as expected, with an L1 error norm of 0.
