# 3D Sod Shock Test
Illustrates the ability of a code to resolve shocks and contact discontinuities over a narrow region. The test consists of two constant states (on left pressure and density are equal to 1; on right they are equal to 0.1) separated by a discontinuity at 0.5. Gamma is set to 1.4. This test is performed with the default hydro build (`cholla/builds/make.type.hydro`).
## Parameter file: (`cholla/examples/3D/sod.txt`)
```
#
# Parameter File for 3D Sod Shock tube
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=100
# number of grid cells in the z dimension
nz=100
# final output time
tout=0.2
# time interval for output
outstep=0.2
# name of initial conditions
init=Riemann
#init=Read_Grid
# domain properties
xmin=0.0
ymin=0.0
zmin=0.0
xlen=1.0
ylen=1.0
zlen=1.0
# type of boundary conditions
xl_bcnd=3
xu_bcnd=3
yl_bcnd=3
yu_bcnd=3
zl_bcnd=3
zu_bcnd=3
# path to output directory
outdir=./

#################################################
# Parameters for 1D Riemann problems
# density of left state
rho_l=1.0
# velocity of left state
vx_l=0.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=1.0
# density of right state
rho_r=0.1
# velocity of right state
vx_r=0.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=0.1
# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.4
```
Upon completion, you should obtain two output files. The initial and final densities (in code units) of a slice along the y-midplane is shown below. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/3dsod_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in z direction vs cells in x direction. The leftmost is the initial density plot with a constant density of 1 throughout all 100 y cells between x-cells 0 through 50 and a constant density of 0.1 between x cells 0 through 100. The rightmost plot is the final density plot at t = 0.20 with a nonconstant density in x and constant density in z. A density of 1 transitions abruptly to a density 0.8 around x = 25 cells, then gradually lessens to 0.6 around x = 50 cells. An abrupt change occurs at x = 70 cells to a density of 0.3 and the final abrupt transition is at x = 90 cells to a density of 0.2" width="1200" />  
A skewer in x along and y and z midplanes yields the traditional 1-dimension solution:  
<img src="./images/3dsod_density_x.png" alt="Two scatter plots side by side of density vs cells in the x direction. The leftmost is the initial density plot with a density of 1 between x-cells 0 through 50 and a density of 0.1 between x cells 0 through 100. The rightmost plot is the final density plot at t = 0.20. A density of 1 transitions abruptly to a density 0.8 around x = 25 cells, then gradually lessens to 0.6 around x = 50 cells. An abrupt change occurs at x = 70 cells to a density of 0.3 and the final abrupt transition is at x = 90 cells to a density of 0.2" width="1200" />  
We can see a rarefaction wave on the left side, followed first by a contact discontinuity and then a shock.
