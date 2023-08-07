# 3D Sound Wave
Shows the propagation of a sound wave through the grid. The test consists of a linear wave of amplitude 1e-4 on a background density of 1.0 and pressure of 0.6. Gamma is set to 1.666666666666667. This test is performed with the default hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Sound_Wave()`

## Parameter file: (`cholla/examples/3D/sound_wave.txt`)
```
#
# Parameter File for sound wave test
#

################################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# final output time
tout=0.05
# time interval for output
outstep=0.01
# name of initial conditions
init=Sound_Wave
# domain properties
xmin=0.0
ymin=0.0
zmin=0.0
xlen=4.0
ylen=4.0
zlen=4.0
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
# Parameters for linear wave problems
# initial density
rho=1.0
# velocity in the x direction
vx=0
# velocity in the y direction
vy=0
# velocity in the z direction
vz=0
# initial pressure
P=0.6
# amplitude of perturbing oscillations
A=1e-4
# value of gamma
gamma=1.666666666666667
```
Upon completion, you should obtain five output files. Currently this test is holding density and pressure constant throughout the entire duration.
