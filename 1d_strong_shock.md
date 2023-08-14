# 1D Strong Shock
This test is similar to the Sod shock tube but has higher initial pressure and density differences. This shows the ability of a code to limit oscillatory behavior in areas of high density and pressure contrasts. The setup consists of a density and pressure of 10.0 and 100.0, respectively, for 0 \< x \< 0.5 and density= pressure = 1.0 for 0.5 \< x \< 1.0. Gamma is set to 1.4. This test was performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (modified from`cholla/examples/1D/strong_shock.txt`)
Modified to add yl_bcnd, yu_bcnd, zl_bcnd, and zu_bcnd=0
```
#
# Parameter File for 1D strong shock test
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.07
# time interval for output
outstep=0.07
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
rho_l=10.0
# velocity of left state
vx_l=0.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=100.0
# density of right state
rho_r=1.0
# velocity of right state
vx_r=0.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=1.0
# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.4
```
Upon completion, you should obtain two output files. The final density and pressure (in code units) of the solution is shown below . Examples of how to extract and plot data can be found in cholla/python_scripts/plot_sod.ipynb.  
<img src="./images/1dstrong-shock_density_pressure.png" alt="Two scatter plots side by side, showing density vs cells in the x direction on the left and pressure vs cells in the x direction on the right. The density plot shows a value of 10.0 remain constant until x = 20 cells, at which it decreases to a value of 3 by x = 55 cells. Here it remains approximately constant until x = 75 cells, wherer it spikes to a value of 5 by x = 80 cells. At x = 85 cells it drops discontinuously to a value of 0.5, where it remains for the last 15 cells. The pressure plot shows a value of 100 until x = 20 cells. Here it gradually decreases to a value of 20 at x = 55 cells, where it remains constant until x = 85 cells. It abruptly drops to almost zero and stays there for the remaining 15 cells. In the upper right hand corner of both plots is the text 't= 0.070'." width="1200" />  

We see a rarefaction expanding from the just after the initial discontinuity, followed by a contact discontinuity at x = 75 cells and a shock at x = 85 cells. There is slight oscillatory behavior around x = 70 cells but it is limited.
