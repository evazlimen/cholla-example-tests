# 3D Ryu and Jones MHD shock tube 1a
This MHD shock tube has five waves and does not indluce alfven waves. For more testing information see [MHD Riemann Problems](https://robertcaddy.com/posts/MHD-Riemann-Problems/). The test consists of a left state with density of 1.0, pressure of 20.0 and velocity of 10.0 $\hat{x}$. The right state consists of a density and pressure of 1.0 and velocity of -10.0 $\hat{x}$. Both sides have a magnetic field  of 1.4104739588693909 $\hat{x}$ + 1.4104739588693909 $\hat{y}$. Gamma is set to 1.6666666666666667 and the initial discontinuity is at 0.5. This test is performed with the mhd build (`cholla/builds/make.type.mhd`). 

## Parameter file: (`cholla/examples/3D/Ryu_and_Jones_1a.txt`)
While the file states that it is for test 4d, it is for test 1a.
```
#
# Parameter File for 3D Ryu & Jones MHD shock tube 4d.
# Citation: Ryu & Jones 1995 "Numerical Magnetohydrodynamics in Astrophysics:
# Algorithms and Tests for One-Dimensional Flow"
#
# Note: There are many shock tubes in this paper. This settings file is
# specifically for shock tube 4d
#

################################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# final output time
tout=0.08
# time interval for output
outstep=0.08
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
rho_l=1.0
# velocity of left state
vx_l=10.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=20.0
# Magnetic field of the left state
Bx_l=1.4104739588693909
By_l=1.4104739588693909
Bz_l=0.0

# density of right state
rho_r=1.0
# velocity of right state
vx_r=-10.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=1.0
# Magnetic field of the right state
Bx_r=1.4104739588693909
By_r=1.4104739588693909
Bz_r=0.0

# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.6666666666666667
```
Upon completion, you should obtain two output files. The initial and final densities (in code units) of a slice along the y-midplane is shown below.  Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/ryu-jones_1a_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a value of 1.0 across all cells. The rightmost plot is the final density plot at t = 0.08 with a constant density in z and nonconstant in x. From left to right, a density of 1 jumps to a value of 2.5 at x = 40 cells, followed by a jump to 3.9 at x = 150 cells and a drop to 3.85 at c = 160 cells. There is a final density drop to 1.0 at x = 225 cells." width="1200" />  
A skewer in x along y and z midplanes yields the 1-dimensional solution (density and total pressure):  
<img src="./images/ryu-jones_1a_density_x.png" alt="On top are two scatter plots side by side of density vs cells in the x direction. The leftmost is the initial density plot with a constant density 1 across all cells. The rightmost plot is the final density plot at t = 0.08. A density of 1 jumps to a value of 2.5 at x = 40 cells, followed by a jump to 3.9 at x = 140 cells and a drop to 3.85 at c = 150 cells. There is a final density drop to 1.0 at x = 225 cells. On bottom there are two scatter plots side by side of total pressure vs cells in the x direction. On the left is the inital pressure function, with a value of 20 from x = 0 to 128 and a value of 1.0 between x = 128 to 256. On the right is the final pressure function, which consists of a value of 1 which jumps to 155 at x = 40 cells. This value remains until x = 150, where it transitions to a value of x = 145. There is a final drop in pressure to 1.0 around x = 225 cells. " width="1200" />  
From left to right, we see a fast shock followed by a slow rarfaction, contact discontinuity, slow shock, and fast shock..
