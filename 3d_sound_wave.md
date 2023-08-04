# 3D Sound Wave
Similar to the Sod shock test but includes magnetic fields. Illustrates the ability of a code to reolve shocks and contact discontinuities over a narrow region. The test consists of two constant states (on left pressure and density are equal to 1; on right they are equal to 0.1 and 0.128, respectively) separated by a discontinuity at 0.5. The left side has a magnetic field of 0.75 $\hat{x}$ + 1 $\hat{y}$ while the right side has a magnetic field of 0.75 $\hat{x}$ - 1 $\hat{y}$. Gamma is set to 2.0. This test is performed with the mhd build (`cholla/builds/make.type.mhd`).

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
Upon completion, you should obtain two output files. The initial and final densities and total pressures (in code units) of a slice along the y-midplane is shown below. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/bio-wu_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a constant density of 1 throughout all 256 z cells between x-cells 0 through 128 and a constant density of 0.128 between x cells 128 through 256. The rightmost plot is the final density plot at t = 0.10 with a nonconstant density in x and constant density in z. A density of 1 begins decreasing around x = 80 cells to around 0.7 but briefly and abruptly jumps to 0.8 around x = 125 cells. It is then constant around 0.7 until x = 150 cells where it jumps to 0.3 and remains constant until x = 175 where it jumps to 0.1." width="1200" />  
<img src="./images/bio-wu_pressure_xz.png" alt="Two 2D histograms side by side, showing pressure of cells in the z direction vs cells in x direction. The leftmost is the initial pressure plot with a constant pressure of 1.8 throughout all 256 z cells between x-cells 0 through 128 and a constant pressure of 0.8 between x cells 128 through 256. The rightmost plot is the final pressure plot at t = 0.10 with a nonconstant pressure in x and constant pressure in z. A pressure of 1.8 begins decreasing around x = 80 cells to around 1.0 but briefly and abruptly jumps to 1.1 around x = 125 cells. It is then constant around 1.0 until x = 150 cells where it jumps to 0.8 and remains constant until x = 200 where it smoothly increases to 1.0." width="1200" />  
A skewer in x along  y and z midplanes yields the 1-dimension solution of density and total pressure:  
<img src="./images/brio-wu_density_x.png" alt="On top are two scatter plots side by side of density vs cells in the x direction. The leftmost is the initial density plot with a constant density of 1 between x-cells 0 through 128 and a constant density of 0.128 between cells 128 and 256. The rightmost plot is the final density plot at t = 0.10 where a density of 1 begins decreasing around x = 80 cells to around 0.7 but briefly and abruptly jumps to 0.8 around x = 125 cells. It is then constant around 0.7 until x = 150 cells where it jumps to 0.3 and remains constant until x = 175 where it jumps to 0.1. Below is two scatter plots side by side of pressure vs cells in the x direction. The leftmost plot is the initial pressure function of 1.8 from cells 0 to 128 and 0.8 from cells 128 to 256. The rightmost plot is the final pressure function, which shows q pressure of 1.8 begin decreasing around x = 80 cells to around 1.0. It briefly and abruptly jumps to 1.1 around x = 125 cells. It is then constant around 1.0 until x = 150 cells where it jumps to 0.8 and remains constant until x = 200 where it smoothly increases to 1.0.. " width="1200" />  
From left to right, we see a fast rarefaction followed by a compound wave, contact discontinuity, slow shock, and a final fast rarefaction.