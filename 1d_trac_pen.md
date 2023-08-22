# 1D Trac-Pen Shock Tube
This test shows the ability of a code to resolve shocks in high mach numbers and is originally from Trac & Pen, 2004. The setup consists of a density and pressure of 11.0 for -3 \< x \< 0 and 0.01. For 0 \< x \< 3.0, density is set to 0.2 and pressure to 0.01. Gamma is set to 1.66666667 and the velocity is 120.0 ('boosted') everywhere. This test was performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Riemann()`. 

## Parameter file: (modified from`cholla/examples/1D/trac_pen.txt`)
Modified to add yl_bcnd, yu_bcnd, zl_bcnd, and zu_bcnd=0
```
#
# Parameter File for 1D Shock tube
# described in Trac & Pen, 2004
#

################################################
# number of grid cells in the x dimension
nx=300
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.8
# time interval for output
outstep=0.8
# name of initial conditions
init=Riemann
# domain properties
xmin=-3.0
ymin=0.0
zmin=0.0
xlen=6.0
ylen=1.0
zlen=1.0
# type of boundary conditions
xl_bcnd=1
xu_bcnd=1
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
vx_l=120.0
vy_l=0.0
vz_l=0.0
# pressure of left state
P_l=1.0
# density of right state
rho_r=0.2
# velocity of right state
vx_r=120.0
vy_r=0.0
vz_r=0.0
# pressure of right state
P_r=0.01
# location of initial discontinuity
diaph=0.0
# value of gamma
gamma=1.66666667
```
Upon completion, you should obtain two output files. The initial and final density, pressure, and velocity (in code units) of the solution is shown below. Examples of how to extract and plot data can be found in cholla/python_scripts/plot_sod.ipynb.  
<img src="./images/1dtrac-pen_6panel_density_pressure.png" alt="Three rows of two scatter plots side by side. The first row shows density vs x position, the second row shows pressure vs x position, and the third row shows velocity vs position. In all rows, the first plot has the text 't = 0.00' in the upper right corner, corresponding to the initial condition, while the second plot has the text 't = 0.80' in the upper right corner and shows the final outcome. All plots range from 0.0 to 1.0 on the x-axis. The initial density plot shows a value of 1.0 for x between 0 and 0.5 and for x between 0.5 and 1. The final density plot shows a value of 0.45 until x = 0.1, where it discontinuously jumps to a value of 1.0. It remains at 1.0 until x = 0.3, where it gradually decreases to a value of 0.45 at x = 0.5. There is a drop at x = 0.6 to a value of 0.4. It increases to a value of 0.7 from x = 0.65 to x = 0.7, then decreases to a value of 0.2 by x = 0.75. At x = 0.8 it jumps to a value of 0.7, then gradually decreases by x = 0.9 to a value of 0.45. The initial pressure plot has a value of 1.0 for x between 0 and 0.5 and 0.01 elsewhere. The final pressure plot shows a value of 0.2 remain constant until x = 0.1, where it jumps discontinuously to a value of 1.0. It remains at 1.0 until x = 0.3, where it gradually decreases to a value of 0.25 by x = 0.5. It remains constant until x = 0.7, where it drops very close to zero, remaning here until x = 0.8. Here it jumps to a value of 0.2 where it remains with a slight downward trend for the last 0.2 in x. The initial velocity plot shows a constant value of 120 for all x. The final velocity plot shows a value of 119 until x = 0.1 where it jumps to 120. It begins to increase at x = 0.3 and reaches a value of 121 by x = 0.5. It decreases to 120 between x = 0.6 and x = 0.7. It decreases again, this time discontinuously, at x = 0.8 to a value of 119. Here is remains with a slight downward trend for the remained of the plot." width="1200" />  

We see a shock, followed by a rarefaction, contact discontinuity, shock, shock, and rarefaction.
It is difficult to discern whether this solution is in agreement with that of Trac and Pen (2004): 
Plot information from Trac and Pen (2004): "In Fig. 1, we compare the results of the static and boosted tests. In Fig. 1(a), the static test results for MACH code (open circles) and Relaxing TVD code (crosses) are plotted against the exact solution (solid lines). The Relaxing TVD results have been shifted both horizontally and vertically for clarity. The plots have been rescaled such that the initial discontinuity is placed at x = 0 and the shock front at x = 1. The grid spacing corresponds to delta x =  0.02"

![trac_pen2004](https://github.com/evazlimen/cholla-example-tests/assets/109487593/b145e2e4-8555-4f00-a585-a09e7051ac47)

By changing the outstep to 0.008, we can also obtain the evolution of the density (here at 8 fps):

https://github.com/evazlimen/cholla-example-tests/assets/109487593/949a5a09-70ad-4b46-9e7e-8c208ed1b651

Information is as of SHA ab36c0f630a82e6eb9ea5e0f43c9e4eb0e81b004.
