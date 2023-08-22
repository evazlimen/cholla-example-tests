# 1D Einfeldt Strong Rarefaction (123 test)
This test highlights a scenario in which linearized Riemann solvers will produce negative densities/pressures without appropriate modifications. This is due to a region of mostly kinetic energy and approaching vacuum pressure. However, `cholla` checks densities/pressure produced by the approximate (Roe) solver and switches to the HLLE solver if needed. This is not an issue with the exact solver. This test is from Toro's *Riemann solvers and numerical methods for fluid dynamics* Sec. 6.3.3, test 2. The test consists of left and right states separated at x = 0.5 with velocities -2 and 2, respectively, moving away from each other. Density = 1.0 and pressure = 0.4 on both sides. Gamma is set to 1.4. This test is performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (**modified** to add y and z boundary conditions = 0 from `cholla/examples/1D/123.txt`)
```
#
# Parameter File for Einfeldt strong rarefaction test (aka 123 problem)
# Parameters derived from Toro, Sec. 6.4.4, test 2
#

################################################
# number of grid cells in the x dimension
nx=128
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.15
# time interval for output
outstep=0.15
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
vx_l=-2.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=0.4
# density of right state
rho_r=1.0
# velocity of right state
vx_r=2.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=0.4
# location of initial discontinuity
diaph=0.5
# value of gamma
gamma=1.4
```
Upon completion, you should obtain 2 output files. The initial and final density, pressure, and velocity (in code units) of the solution is shown below (pink dots) plotted over the exact solution (purple line). Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1d123_6panel_density_pressure.png" alt="Three rows of two scatter plots side by side. The first row shows density vs x position, the second row shows pressure vs x position, and the third row shows velocity vs position. In all rows, the first plot has the text 't = 0.00' in the lower right corner while the second plot has the text 't = 0.15' in the lower right corner. The plots of the first column are shown with pink dots while the plots of the second column have pink dots plotted over a purple line. In all cases, the pink dots match the shape of the purple line, very closely for the first two rows and imperfectly for the velocity plot. The initial density plot shows a constant density of 1 while the final concave up parabola centered on the x-axis, with a maximum of 1 and a minimum approaching zero. The edges of the parabola at the maximum flatten and are approximately constant from 0 to 0.1 and 0.9 to 1, extending to the edge of the plot. The intial pressure plot shows a constant value of 0.4, while the final shows a similar parabola with the same maximum and minimums. However, at the minimum, the region is much flatter from x = 0.3 to 0.7 with a pressure approaching zero. The initial velocity plot shows a value of -2 between x = 0 and 0.5 and a value of 2 between x = 0.5 and 1.0. The final plot has a value of -2 from x = 0 to x = 0.1, then increases steadily to a value of 0 by x = 0.45. It remains at zero until x = 0.55, when it begins to increase to a value of 2 by x = 0.9. It is constant there until 1.0." width="1200" />  

We see that the two rarefaction waves have moved outwards, away from each other, leaving behind a region of low density and low pressure. 
