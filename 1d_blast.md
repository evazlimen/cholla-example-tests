# 1D Blast Wave
This test is designed to assess the performance of a code near strong shocks and contact discontinuities. The test consists of three regions. For x < 0.1, pressure is set to 1000.0. For x > 0.9, pressure is set to 100. Everywhere else, pressure is set to 0.01. Density is set to 1.0 everywhere and velocity everywhere is zero. Gamma is set to 1.4. This test is performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Blast_1D()`. 

## Parameter file: (`cholla/examples/1D/blast_1D.txt`)
```
#
# Parameter File for the 1D interacting blast wave test from
#     Woodward & Collela, 1984. See also Stone et al., 2008, Section 8.1
#

######################################
# number of grid cells in the x dimension
nx=400
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.038
# time interval for output
outstep=0.00038
# value of gamma
gamma=1.4
# name of initial conditions
init=Blast_1D
# domain properties
xmin=0.0
ymin=0.0
zmin=0.0
xlen=1.0
ylen=1.0
zlen=1.0
# type of boundary conditions
xl_bcnd=2
xu_bcnd=2
yl_bcnd=0
yu_bcnd=0
zl_bcnd=0
zu_bcnd=0
# path to output directory
outdir=./
```
Upon completion, you should obtain 101 output files. The final density and pressure (in code units) of the solution is shown below .  Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1dblast_density_pressure.png" alt="Two scatter plots side by side, showing density vs cells in the x direction on the left and pressure vs cells in the x direction on the right. The density plot shows a curve increasing slightly from close to zero to around a value of 0.2 at x = 225, then jumping to a value of 2, reaching this value at x = 250. Here it jumps discontinously to 5, then decreases rapidly but continuously to 4 at x = 260 and then again to 3 at x = 290. It abruptly jumps at x = 300 to a value of 6, then jumps down to a value of 0.5. At x = 350 it jumps again to 0.2. The pressure plot shows a curve with value of 80 increasing to 110 by x = 250. It then jumps discontinously to a value of 400 and then decreases smoothly until x = 300 to a value of 100. It remains at 100 until x = 350 at which it drops to 10. In the upper right hand corner of both plots is the text 't= 0.038'." width="1200" />  

We see a contact discontinuity around x = 225 cells followed by a shock at x = 250 and a rarefaction fan. We have a contact discontinuity just past x = 300 cells and a shock at x = 350. 

We can also obtain the evolution of the density (here at 10 fps):


