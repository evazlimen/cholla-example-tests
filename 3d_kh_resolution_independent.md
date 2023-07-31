# 3D Resolution Independent Kelvin-Helmholtz test
This test highlights the ability of a code to resolve mixing caused by shear flows, emphasizing the importance of an efficient, high order reconstuction method and a fast code. In general, the level of mixing would increase with the resolution; however, this is a resolution independent version. The test consists of a region of higher density (100) sandwiched between two regions of lower density (1.0). The high density layer has a velocity of 10.5 and the low density layers have a velocity of 9.5. Pressure is set to 2.5 and a 1% pertubation (amplitude of 0.1) is added to the high denisty layer to provoke the instability. Gamma is set to 1.4. This test is performed with the default hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `KH_res_ind()`.

## Parameter file: (`cholla/examples/3D/KH_res_ind_3D.txt`)
```
#
# Parameter File for the 3D resolution independent Kelvin-Helmholtz test.
#

######################################
# number of grid cells in the x dimension
nx=128
# number of grid cells in the y dimension
ny=128
# number of grid cells in the z dimension
nz=128
# final output time
tout=5.0
# time interval for output
outstep=0.01
# value of gamma
gamma=1.6666666666666667
# name of initial conditions
init=KH_res_ind
# domain properties
xmin=0.0
ymin=-0.5
zmin=-0.5
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
```
Upon completion, you should obtain 501 output files. The initial and final densities (in code units) of a slice along the y-midplane is shown below. Note the differing scales of the colorbars. Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/kh_res_ind_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a constant density in x and nonconstant in z. The center region, from roughly z = 30 to z= 70, has a density of 100 while the remaining regions have a density of 1.0. There is a small gradient over around 5 cells on either side of the high density region where the density decreases The rightmost plot is the final density plot at t = 5.00 with a nonconstant density in both x and z. The low and high density fluids have partially mixed, forming eddies, and creating a pattern resembling 3 sideways Vs pointing towards the right. The Vs are fuzzy and discontinous. There is an area of much higher density around the z midplane and x =  80." width="1200" />  
We see that eddies have formed as a result. The mixing is highly symmetrical and forms a repeating pattern.
