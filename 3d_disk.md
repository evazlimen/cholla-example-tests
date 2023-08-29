# 3D Disk
This models the Milky Way's stellar disk. Gamma is set to 1.666666667. Full initial conditions can be found in `cholla/src/model/disk_ICs.cpp`under `Disk_3D()`. This test is performed with the disk build (`cholla/builds/make.type.disk`).  

## Parameter file: (`cholla/examples/3D/Disk.txt`)
```
#
# Parameter File for a 3D disk
#

######################################
# number of grid cells in the x dimension
nx=512
# number of grid cells in the y dimension
ny=512
# number of grid cells in the z dimension
nz=512
# final output time
tout=50000
# time interval for output
outstep=100
# value of gamma
gamma=1.6666667
# name of initial conditions
init=Disk_3D
n_hydro=10
# domain properties
xmin=-5
ymin=-5
zmin=-5
xlen=10
ylen=10
zlen=10
# type of boundary conditions
xl_bcnd=3
xu_bcnd=3
yl_bcnd=3
yu_bcnd=3
zl_bcnd=3
zu_bcnd=3
# rotated projection properties
nxr=384
nzr=384
delta=0.0
theta=20.0
phi=20.0
Lx=15.0
Lz=15.0
flag_delta=2
ddelta_dt=-0.001
# path to output directory
outdir=./
```
Upon completion, you should obtain 501 output files. Currently this test is producing a grid of zero density, zero energy, and undefined pressure for the entirety of the run.  

Note that the 2D disk, which does run, has its initial conditions set in `cholla/src/grid/initial_conditions.cpp`.