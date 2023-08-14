# 1D Shu and Osher test
This test highlights the ability of a code to revole small scale smooth flow and shocks simultaneously. Further, it shows how lower resolution solutions can cut off some of the amplitude of maxima due to the slope limiters. The test consists of left and right states separated at x = -0.8. On the left, density is set to 3.857143, pressure to 10.33333, and velocity to 2.629369. On the right, density is sinusoidally varying: $\rho(x)$ =  1.0 + 0.2 $\sin(5.0\pi x)$. Pressure is set to 1.0 and the velocity is 0.0. Gamma is set to 1.4. This test is performed with the hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Shu_Osher()`. 

## Parameter file: (**modified** from `cholla/examples/1D/Shu_Osher.txt`)
Modified to add yl_bcnd, yu_bcnd, zl_bcnd, and zu_bcnd=0. Xmin changed to -1.0 and xlen to 2.0.
```
# Parameter File for the Shu-Osher shock tube test, originally from
#     Shu & Osher, 1989. These parameters are from Stone et al., 2008, Section 8.1
#

######################################
# number of grid cells in the x dimension
nx=200
# number of grid cells in the y dimension
ny=1
# number of grid cells in the z dimension
nz=1
# final output time
tout=0.47
# time interval for output
outstep=0.47
# value of gamma
gamma=1.4
# name of initial conditions
init=Shu_Osher
# domain properties
xmin=-1.0
ymin=0.0
zmin=0.0
xlen=2.0
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
```
Upon completion, you should obtain 2 output files. The initial and final density and pressure (in code units) of the solution is shown below. Examples of how to extract and plot data can be found in `cholla/python_scripts/plot_sod.ipynb`.  
<img src="./images/1dshu-osher_density_pressure.png" alt="Two rows of two scatter plots side by side. The first row shows density vs cells in the x direction while the second shows pressure vs cells in the x direction. The first column of each row shows the initial density/pressure, with the text 't = 0.00' in the upper right corner of both plots. The second row shows the final outcomes, with the text 't = 0.47' in the upper right corner of both plots. The initial density plot (row 1 column 1) has a value of 3.857143 for x <-.8 and a sine wave of 1 + .2sin(5.0*pi*x) for all other x. The final density plot has a smashed, irregular wave going from lower density to a maximum of 3 around x = 160. From x = 175-200 a piece of the orginal sine wave remains. For the pressure plots (row 2), the intial plot has a value of 10.33333 for x <-.8 and 1 otherwise. The final plot has function that increases from left to right to a maximum of 6 at x = 175, then discontinuously jumps to 1" width="1200" />   

Notably,as of SHA ab36c0f630a82e6eb9ea5e0f43c9e4eb0e81b004, this solution does not match that of Schneider and Robertson 2015 or Stone et al. 2008, shown below:

![stone2008shu-osher](https://github.com/evazlimen/cholla-example-tests/assets/109487593/8438b662-4e15-4fd3-ab90-a802a7b8bce0)
