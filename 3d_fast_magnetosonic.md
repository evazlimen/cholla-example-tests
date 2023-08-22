# 3D Fast Magnetosonic
Illustrates the ability of a code to handle a low frequency compression wave. The test consists of an initial density of 1.0, pressure of 0.6, and zero initial velocity. A magnetic field is initialized to $\hat{x}$ + 1.5 $\hat{y}$ and a linear wave is set with amplitude 1e-6. Gamma is set to 1.666666666666667. This test is performed with the mhd build (`cholla/builds/make.type.mhd`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Linear_Wave()`.

## Parameter file: (`cholla/examples/3D/fast_magnetosonic.txt`)
```
#
# Parameter File for MHD fast magnetosonic wave
# See [this blog post](https://robertcaddy.com/posts/Classes-and-bugfixing-6/)
# for details on each wave.
# The right eigenvector for this wave is:
# (1/(6*sqrt(5))) * [6, +/-12, -/+4*sqrt(2), -/+2, 0,  8*sqrt(2), 4, 27]
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
tout=0.5
# time interval for output
outstep=0.5
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
rEigenVec_rho=0.4472135954999579
rEigenVec_MomentumX=0.8944271909999159
rEigenVec_MomentumY=-0.4472135954999579
rEigenVec_MomentumZ=0.0
rEigenVec_Bx=0.0
rEigenVec_By=0.8944271909999159
rEigenVec_Bz=0.0
rEigenVec_E=2.0124611797498106
```
Upon completion, you should obtain two output files. With outstep = 0.01 you will obtain 51 outputs and can obtain the evolution of the total magnetic field and the total presure (here at 10 fps): Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  

https://github.com/evazlimen/cholla-example-tests/assets/109487593/b0ae49ce-7540-4f72-9e7a-1334c81ce720

https://github.com/evazlimen/cholla-example-tests/assets/109487593/3e8ee5b8-2214-4a4f-a74b-21d46bf8cea2

As expected for a fast magnetosonic wave, we see that the magnetic and pressure oscillations are in phase.
