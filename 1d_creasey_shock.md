# 1D Creasey shock tube test
This test highlights a scenario in which gas is allowed to cool radiatively, forming a dense region downstream from the shock. The test consists of identical left and right states. Everywhere, density is set to 1.672622e-24 and pressure to 1.380658e-10.
Gamma is set to 1.666666667 and the initial velocity of both sides is zero. This test is performed with the cooling build (?) (`cholla/builds/make.type.cooling`) but no difference was found with the hydro build. Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (**modified** to add y and z boundary conditions = 0 from `cholla/examples/1D/Creasey_shock.txt`)
```
#
# Parameter File for 1D shock tube test
# described in Creasey 2011
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=30.0
# time interval for output
outstep=0.1
# name of initial conditions
init=Riemann
# domain properties
xmin=0.0
ymin=0.0
zmin=0.0
xlen=3.08567758e18
ylen=3.08567758e18
zlen=3.08567758e18
# type of boundary conditions
xl_bcnd=3
xu_bcnd=3
# path to output directory
outdir=./

#################################################
# Parameters for 1D Riemann problems
# density of left state
rho_l=1.672622e-24
# velocity of left state
vx_l=0.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=1.380658e-10
# density of right state
rho_r=1.672622e-24
# velocity of right state
vx_r=0.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=1.380658e-10
# location of initial discontinuity
diaph=0.0
# value of gamma
gamma=1.666666667
```
Upon completion, you should obtain 300 output files. The initial and final density and pressure (in code units) of the solution is shown below.  Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1dcreasey-shock_density_pressure.png" alt="Two rows of two scatter plots side by side. The first row shows density vs cells in the x direction while the second shows pressure vs cells in the x direction. The first column of each row shows the initial density/pressure, with the text 't = 0.00' in the upper right corner of both plots. The second row shows the final outcomes, with the text 't = 30.0' in the upper right corner of both plots. The initial plots are identical to the final plots for both density and pressure. Density is constant at 1.672622e-24 and pressure is constant at 1.380658e-10." width="1200" />  

Currently (SHA ab36c0f630a82e6eb9ea5e0f43c9e4eb0e81b004), this test is producing a constant density and pressure for the duration. The left and right sides are identical, with zero initial velocity.
