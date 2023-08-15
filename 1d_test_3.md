# 1D Test 3 (strong shock test)
This test is similar to the strong shock test but with only an initial pressure discontinuity. This shows the ability of a code to resolve contacts. The setup consists of a pressure of 1000 for 0 \< x \< 0.5 and 0.01 for 0.5 \< x \< 1.0. Gamma is set to 1.4 and density is 1.0 everywhere. This test was performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (modified from`cholla/examples/1D/test_3.txt`)
Modified to add yl_bcnd, yu_bcnd, zl_bcnd, and zu_bcnd=0
```
#
# Parameter File for test 3 (strong shock test)
# Parameters derived from Toro, Sec. 6.4.4, test 3
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.012
# time interval for output
outstep=0.012
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
yl_bcnd=0
yu_bcnd=0
zl_bcnd=0
zu_bcnd=0
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
P_l=1000
# density of right state
rho_r=1.0
# velocity of right state
vx_r=0.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=0.01
# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.4
```
Upon completion, you should obtain two output files. The final density and pressure (in code units) of the solution is shown below . Examples of how to extract and plot data can be found in cholla/python_scripts/plot_sod.ipynb.  
<img src="./images/1dtest-3_density_pressure.png" alt="Two scatter plots side by side, showing density vs cells in the x direction on the left and pressure vs cells in the x direction on the right. The density plot shows a value of 1.0 gradually decrease to 0.1 by x = 40 cells, where it reamins constant until x = 70 cells. Here it jumps to a value of 6 before dropping back down to a value of 1. The width of the spike is around 10 cells. The density remains at 1 for the remainder of the grid. The pressure plot shows a value of 1000 gradually decrease to 450 by x = 40 cells. Here it remains approximately constant until x = 80 cells where it drops discontinuously to a value approaching zero. In the upper right hand corner of both plots is the text 't= 0.012'." width="1200" />  

We see a contact discontinuity follow directly by a shock. This solution is in agreement with that of Toro test 3, shown below:
![toro2013test3](https://github.com/evazlimen/cholla-example-tests/assets/109487593/0eb33a5e-331a-4548-bfff-a492378e959e)

Interestingly, it better matches the expected Liska and Wendroff 2003 test 3a ('stationary') solution than stationary parameter file: see [stationary](https://github.com/evazlimen/cholla-example-tests/blob/main/1d_stationary.md) and 
![liskawendroff2003-test3a](https://github.com/evazlimen/cholla-example-tests/assets/109487593/892728ed-2ed6-433e-ab83-059f99238149)
