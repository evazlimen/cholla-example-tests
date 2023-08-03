# 3D Alfven Wave
This is a quantitative test of linear planar waves oblique to the grid. The test consists of a linear wave with amplitude of 1e-6 on a density of 1.0, pressure of 0.6, and magnetic field of $\hat{x}$ + 1.5 $\hat{y}$. This test is performed with the mhd build (`cholla/builds/make.type.mhd`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Linear_Wave()`. 

## Parameter file: (`cholla/examples/3D/alfven_wave.txt`)
```
#
# Parameter File for MHD Alfven Wave
# See [this blog post](https://robertcaddy.com/posts/Classes-and-bugfixing-6/)
# for details on each wave
# The right eigenvector for this wave is:
# (1/3) * [0, 0, +/-1, -/+2*sqrt(2), 0, -1, 2*sqrt(2), 0]
# The terms with two sign options: use the left one for right moving waves and
# the right one for left moving waves
#

################################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# final output time
tout=1.0
# time interval for output
outstep=1.0
# name of initial conditions
init=Linear_Wave
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
# Parameters for linear wave problems
# initial density
rho=1.0
# velocity in the x direction
vx=0
# velocity in the y direction
vy=0
# velocity in the z direction
vz=0
# initial pressure
P=0.6
# magnetic field in the x direction
Bx=1
# magnetic field in the y direction
By=1.5
# magnetic field in the z direction
Bz=0
# amplitude of perturbing oscillations
A=1e-6
# value of gamma
gamma=1.666666666666667
# The right eigenvectors to set the wave properly
rEigenVec_rho=0
rEigenVec_MomentumX=0
rEigenVec_MomentumY=0
rEigenVec_MomentumZ=-1
rEigenVec_Bx=0
rEigenVec_By=0
rEigenVec_Bz=1
rEigenVec_E=0
```
Upon completion, you should obtain 2 output files. By changing the outstep to 0.01, you will obtain 101 output files and can obtain the evolution of the density (here at 10 fps):



We see the loop moving to the upper right, prompting fluctuations in the background as it transitions out of view before returning in the lower left. 
