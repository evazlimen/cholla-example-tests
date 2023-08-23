# 1D Constant
This test ensures the code can create and maintain a uniform density and pressure, both in space and time. Density is set to 1e4 and pressure to 1.380658e-5 everywhere. Gamma is set to 1.4. This test was performed with the hydro build (`cholla/builds/make.type.hydro`) as the given initial magnetic field is zero. Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Constant()`. 

## Parameter file: (`cholla/examples/1D/constant.txt`)
```
#
# Parameter File for box filled with gas
#

################################################
# number of grid cells in the x dimension
nx=10
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
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
Bx=0.0
By=0.0
Bz=0.0
# value of gamma
gamma=1.666666667
```
Upon completion, you should obtain two output files. The final density and pressure (in code units) of the solution is shown below .  Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1dconstant_density_pressure.png" alt="Two rows of two scatter plots side by side. The first row shows density vs cells in the x direction while the second shows pressure vs cells in the x direction. The first column of each row shows the initial density/pressure, with the text 't = 0' in the upper right corner of both plots. The second row shows the final outcomes, with the text 't = 100000' in the upper right corner of both plots. The initial plots are identical to the final plots for both density and pressure. Density is constant at 1e4 and pressure is constant at 1.380658e-5." width="1200" />  

We obtain a box of gas that is both constant in time and uniform in space. The L1 error norm for the difference between initial and final states is zero for both density and pressure. 

