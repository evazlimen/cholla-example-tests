# 1D Square Wave
This test initializes a square wave density pertubation. The setup consists of an initial density and pressure of 1.0 and 0.01, respectively. A square wave is initialized with amplitude 1.5. Gamma is set to 1.666666666666667. This test was performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Square_Wave()`. 

## Parameter file: (modified from`cholla/examples/1D/square_wave.txt`)
Modified to add yl_bcnd, yu_bcnd, zl_bcnd, and zu_bcnd=0
```
#
# Parameter File for square wave test
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=1.0
# time interval for output
outstep=0.01
n_hydro=1
# name of initial conditions
init=Square_Wave
# size of domain
xmin=0.0
ymin=0.0
zmin=0.0
xlen=1.0
ylen=1.0
zlen=1.0
# type of boundary conditions
xl_bcnd=1
xu_bcnd=1
yl_bcnd=0
yu_bcnd=0
zl_bcnd=0
zu_bcnd=0
# path to output directory
outdir=./

#################################################
# Parameters for square wave 
# initial density 
rho=1.0
# velocity in the x direction 
vx=1.0
# velocity in the y direction
vy=0
# velocity in the z direction
vz=0
# initial pressure 
P=0.01
# relative amplitude of overdense region 
A=1.5
# value of gamma
gamma=1.666666666666667
```
Upon completion, you should obtain 101 output files. We can obtain the evolution of the density (here at 10 fps). Pressure is constant to the $10^{-14}$ level. Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  

We see a square waveform of amplitude 1.5 propagating rightwards.
