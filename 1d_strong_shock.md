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
Upon completion, you should obtain two output files.  The initial and final density, pressure, and velocity (in code units) of the solution is shown below (pink dots) plotted over the exact solution (purple line). Examples of how to extract and plot data can be found in cholla/python_scripts/plot_sod.ipynb.  
<img src="./images/1dstrong-shock_6panel_density_pressure.png" alt="Three rows of two scatter plots side by side.  The first row shows density vs x position, with the leftmost plot showing the initial and the rightmost the final. The second and third rows are the same for pressure and velocity, respectively. In all rows, the first plot has the text 't = 0.00' in the upper right corner while the second plot has the text 't = 0.07' in the upper right corner. The plots of the first column are shown with pink dots while the plots of the second column have pink dots plotted over a purple line. In all cases, the pink dots match the shape of the purple line, albeit imperfectly. The initial density plot shows a value of 10.0 for x between 0.0 and 0.5 and a value of 1.0 elsewhere. The final density plot shows a value of 10.0 remain constant until x = 0.2, at which it decreases to a value of 3 by x = 0.55. Here it remains approximately constant until x = 0.75, where it spikes to a value of 5 by x = 0.8 cells. At x = 0.85 it drops discontinuously to a value of 0.5, where it remains for the last 0.15 in x. The initial pressure plot shows a value of 100 for x between 0 and 0.5 and a value of 1.0 elsewhere. The final pressure plot shows a value of 100 until x = 0.2. Here it gradually decreases to a value of 20 at x = 0.55, where it remains constant until x = 0.85. It abruptly drops to almost zero and stays there for the remaining 0.15 in x. The initial velocity plot shows a value of zero for all x. The final velocity plot shows a value of zero from x = 0.0 to x = 0.2, where it begins to increase to a value of 4 by x = 0.55. It remains at 4 until x = 0.8, where it drops back to a value of zero." width="1200" />  

We see a rarefaction expanding from just after the initial discontinuity, followed by a contact discontinuity at x =0.75 and a shock at x = 0.85. There is very slight oscillatory behavior around x = 0.7 but it is limited.
