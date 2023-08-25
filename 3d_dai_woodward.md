# 3D Dai and Woodward MHD Shocktube
This test highlights the ability of a code to resolve all seven MHD waves. Parameters from  Dai & Woodward 1998. For more testing information see [MHD Riemann Problems](https://robertcaddy.com/posts/MHD-Riemann-Problems/). The test consists of two initally moving states (on left pressure is equal to 0.95 and density is equal to 1.08; on right they are both equal 1.0) separated by a discontinuity at 0.5. The left side has a magnetic field of 0.5641895835477563 $\hat{x}$ + 1.0155412503859613 $\hat{y}$ + 0.5641895835477563 $\hat{z}$ while the right side has a magnetic field of 0. 5641895835477563 $\hat{x}$ + 1.1283791670955126 $\hat{y}$ + 0.5641895835477563 $\hat{z}$. Gamma is set to 1.6666666666666667. This test is performed with the mhd build (`cholla/builds/make.type.mhd`).

## Parameter file: (`cholla/examples/3D/Dai_and_Woodward.txt`)
```
#
# Parameter File for 3D Dai & Woodward MHD shock tube
# Citation: Dai & Woodward 1998 "On The Diverrgence-Free Condition and
# Conservation Laws in Numerical Simulations for Supersonic Magnetohydrodynamic
# Flows"
#

################################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# final output time
tout=0.2
# time interval for output
outstep=0.2
# name of initial conditions
init=Riemann

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
rho_l=1.08
# velocity of left state
vx_l=1.2
vy_l=0.01
vz_l=0.5
# pressure of left state
P_l=0.95
# Magnetic field of the left state
Bx_l=0.5641895835477563
By_l=1.0155412503859613
Bz_l=0.5641895835477563

# density of right state
rho_r=1.0
# velocity of right state
vx_r=0.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=1.0
# Magnetic field of the right state
Bx_r=0.5641895835477563
By_r=1.1283791670955126
Bz_r=0.5641895835477563

# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.6666666666666667
```
Upon completion, you should obtain two output files. The initial and final densities (in code units) of a slice along the y-midplane is shown below. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/dai-woodward_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a constant density of 1.08 throughout all 256 y cells between x-cells 0 through 128 and a constant density of 0.95 between x cells 128 through 256. The rightmost plot is the final density plot at t = 0.20 with a nonconstant density in x and constant density in z. A density of 1.08 abruptly increases to 1.5 at x = 80 cells, followed by a second jump to a density of 1.6 at x = 140 cells. It drops back down to 1.5 at x = 150 and drops again to 1.3 at x = 175. It has a final drop at x = 240 to a denisty of 0.95." width="1200" />  
A skewer in x along  y and z midplanes yields the 1-dimensional solution. $\theta$ is defined as $\arctan\frac{B_{z}}{B_{y}}:  
<img src="./images/3d-dai-woodward_9panel_density_pressure.png" alt="Nine scatter plots showing density, total pressure, energy, vx, vy, vz, by, bz, and theta. The density plot shows density of 1.08 abruptly increases to 1.5 at x = 80 cells, followed by a second jump to a density of 1.6 at x = 140 cells. It drops back down to 1.5 at x = 150 and drops again to 1.3 at x = 175. It has a final drop at x = 240 to a denisty of 0.95. Below are two scatter plots side by side of total pressure. The pressure plot consists of a value of 1.5 until x = 80 where it jumps to 2.7. It jumps less abruptly again at x = 140 to 2.8 and symmetrically drops back down to 2.7 at x = 175. It has a final drop at x = 240 to a value of 1.6. " width="1200" />  
We can compare to Miniati & Martin 2011 (note that they are plotting gas pressure, not total pressure):
<img src="./images/dai-woodward.png" width="1200" />  
From left to right, we see a fast shock followed by Alfven/rotation waves, a slow shock, contact discontinuity, slow shock, alfven/roation waves, and a fast shock
