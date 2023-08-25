# 3D Constant
This models a box filled with gas under a constant magnetic field. The test consists a density of 1e4 and pressure of 1.380658e-5 with a magnetic field initialized as 1.0e-5 $\hat{x}$ + 2.0e-5 $\hat{x}$ + 3.0e-5 $\hat{x}$. Gamma is set to 1.666666667. This test is performed with the mhd build (`cholla/builds/make.type.mhd`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Constant()`. 

## Parameter file: (`cholla/examples/3D/Constant.txt`)
```
#
# Parameter File for 3D box filled with gas
#

################################################
# number of grid cells in the x dimension
nx=10
# number of grid cells in the y dimension
ny=10
# number of grid cells in the z dimension
nz=10
# final output time
tout=100000.0
# time interval for output
outstep=100000.0
# name of initial conditions
init=Constant
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
outdir=./

#################################################
# density
rho=1e4
# velocity
vx=0
vy=0
vz=0
# pressure
P=1.380658e-5
# Magnetic Field
Bx=1.0e-5
By=2.0e-5
Bz=3.0e-5
# value of gamma
gamma=1.666666667
```
Upon completion, you should obtain 2 output files. The pressure, density, and magnetic fields all remain constant over the grid for the duration of the integration. The L1 error norm for pressure, density, all three components of velocity, and all three components of magnetic field is zero.
