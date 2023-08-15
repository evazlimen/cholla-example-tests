# 1D Two Shocks
This test highlights a collision between two shocks. The test consists of left and right states separated at x = 0.4 with velocities 19.5975 and -6.19633, respectively. Density of the left side is 5.99924 and pressure is 460.894. For the right side, density is 5.99242 while pressure is 46.095. Gamma is set to 1.4. This test is performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (**modified** to add y and z boundary conditions = 0 from `cholla/examples/1D/two_shocks.txt`)
```
#
# Parameter File for Toro test 4, a collision of two shocks.
# Parameters derived from Toro, Sec. 6.4.4, test 4
#

################################################
# number of grid cells in the x dimension
nx=100
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.035
# time interval for output
outstep=0.035
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
rho_l=5.99924
# velocity of left state
vx_l=19.5975
vy_l=0.0
vz_l=0.0

# pressure of left state
P_l=460.894
# density of right state
rho_r=5.99242
# velocity of right state
vx_r=-6.19633
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=46.095
# location of initial discontinuity
diaph=0.4
# value of gamma
gamma=1.4
```
Upon completion, you should obtain 2 output files. The final density and pressure (in code units) of the solution is shown below .  Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1dtwo-shocks_density_pressure.png" alt="Two scatter plots side by side, showing density vs cells in the x direction on the left and pressure vs cells in the x direction on the right. The density plot shows a value of 0.1 for x = 0 to x = 20. It then jumps to a value of 2.5. It gradually inceases until x = 65 cells to a value of 7. From this point it resembles a concave down parabola with maximum of 24 at x = 75and width of 20. It has a mininum at x = 85 of 0.2. It then gradually decreases to 0.1 by x = 100. The pressure plot is similar, with a constant value of 0.1 until x = 20, followed by a jump to a value of 180. It then gradually increases up to a value of 1100 at x = 75, and decreases to a value of 600 at x = 85. It then drops to 0.1.. In the lower right hand corner of both plots is the text 't= 0.035'." width="1200" />  

We see a shock, followed by a rarefaction and another shock. This is in contrast to Toro's solution which finds a shock, contact discontinuity, and a shock, and can be seen below:
