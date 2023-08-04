# 3D MHD Blast
Illustrates the ability of the code to handle low $\beta$ plasma problems with strong MHD waves. High performace highlighted through the preservation of initial flow symmetry. This test involves a centrally overpressurized region exploding into a low pressure and low $\beta$ medium. The background density and pressure are 1.0 and 0.1. Inside the blast region of radius 0.1 the pressure is 10.0. The magnetic field is initialized to $\frac{1}{\sqrt{2}}$($\hat{x}$ + $\hat{y}$). Gamma is set to 1.666666666666667. This test is performed with the mhd build (`cholla/builds/make.type.mhd`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `MHD_Spherical_Blast()`. 

## Parameter file: (`cholla/examples/3D/mhd_blast.txt`)
```
#
# Parameter File for the MHD Blast wavelength
# See [Stone & Gardiner 2009](https://ui.adsabs.harvard.edu/abs/2009NewA...14..139S/abstract) for details.
#

################################################
# number of grid cells in the x dimension
nx=200
# number of grid cells in the y dimension
ny=300
# number of grid cells in the z dimension
nz=200
# final output time
tout=0.2
# time interval for output
outstep=0.2
# name of initial conditions
init=MHD_Spherical_Blast
# domain properties
xmin=-0.5
ymin=-0.75
zmin=-0.5
xlen=1.0
ylen=1.5
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
# Parameters for MHD Blast Wave problem

# initial density
rho=1.0
# velocity in the x direction
vx=0.0
# velocity in the y direction
vy=0.0
# velocity in the z direction
vz=0.0
# initial pressure outside the blast zone
P=0.1
# initial pressure inside the blast zone. Note that the paper says this should be 100, that is a typo
P_blast=10.0
# The radius of the blast zone
radius=0.1
# magnetic field in the x direction. Equal to 1/sqrt(2)
Bx=0.70710678118654746
# magnetic field in the y direction. Equal to 1/sqrt(2)
By=0.70710678118654746
# magnetic field in the z direction
Bz=0.0

# value of gamma
gamma=1.666666666666667
```
Upon completion, you should obtain two output files. The initial and final densities and total pressures (in code units) of a slice along the y-midplane is shown below. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
this still needs to be done
<img src="./images/bio-wu_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a constant density of 1 throughout all 256 z cells between x-cells 0 through 128 and a constant density of 0.128 between x cells 128 through 256. The rightmost plot is the final density plot at t = 0.10 with a nonconstant density in x and constant density in z. A density of 1 begins decreasing around x = 80 cells to around 0.7 but briefly and abruptly jumps to 0.8 around x = 125 cells. It is then constant around 0.7 until x = 150 cells where it jumps to 0.3 and remains constant until x = 175 where it jumps to 0.1." width="1200" />  
<img src="./images/bio-wu_pressure_xz.png" alt="Two 2D histograms side by side, showing pressure of cells in the z direction vs cells in x direction. The leftmost is the initial pressure plot with a constant pressure of 1.8 throughout all 256 z cells between x-cells 0 through 128 and a constant pressure of 0.8 between x cells 128 through 256. The rightmost plot is the final pressure plot at t = 0.10 with a nonconstant pressure in x and constant pressure in z. A pressure of 1.8 begins decreasing around x = 80 cells to around 1.0 but briefly and abruptly jumps to 1.1 around x = 125 cells. It is then constant around 1.0 until x = 150 cells where it jumps to 0.8 and remains constant until x = 200 where it smoothly increases to 1.0." width="1200" />  
A skewer in x along  y and z midplanes yields the 1-dimension solution of density and total pressure:  
<img src="./images/brio-wu_density_x.png" alt="On top are two scatter plots side by side of density vs cells in the x direction. The leftmost is the initial density plot with a constant density of 1 between x-cells 0 through 128 and a constant density of 0.128 between cells 128 and 256. The rightmost plot is the final density plot at t = 0.10 where a density of 1 begins decreasing around x = 80 cells to around 0.7 but briefly and abruptly jumps to 0.8 around x = 125 cells. It is then constant around 0.7 until x = 150 cells where it jumps to 0.3 and remains constant until x = 175 where it jumps to 0.1. Below is two scatter plots side by side of pressure vs cells in the x direction. The leftmost plot is the initial pressure function of 1.8 from cells 0 to 128 and 0.8 from cells 128 to 256. The rightmost plot is the final pressure function, which shows q pressure of 1.8 begin decreasing around x = 80 cells to around 1.0. It briefly and abruptly jumps to 1.1 around x = 125 cells. It is then constant around 1.0 until x = 150 cells where it jumps to 0.8 and remains constant until x = 200 where it smoothly increases to 1.0.. " width="1200" />  
From left to right, we see a fast rarefaction followed by a compound wave, contact discontinuity, slow shock, and a final fast rarefaction.
