# 3D Spherical Overpressure
This test illustrates the ability of a code to handle a spherical explosion due to spherical overdensity and overpressure. The test consists of a sphere of radius 0.2 centered at (0.5, 0.5, 0.5) with a density of 1 and pressure of 11, surrounded by a background density and pressure of 0.1 and 1, respectively. This test was performed with the default hydro build (`cholla/builds/make.type.hydro`). Full initial conditions can be found in `cholla/src/grid/initial_conditions.cpp`under `Spherical_Overpressure_3D()`. 

## Parameter file: (`cholla/examples/3D/Spherical_Overpressure.txt`)
Note that the output directory needs to be changed for the user.
```
#
# Parameter File for the 3D Sphere Overpressure.
#

######################################
# number of grid cells in the x dimension
nx=256
# number of grid cells in the y dimension
ny=256
# number of grid cells in the z dimension
nz=256
# output time
tout=0.1
# how often to output
outstep=0.01
# value of gamma
gamma=1.66666667
# name of initial conditions
init=Spherical_Overpressure_3D
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
#outdir=/gpfs/alpine/scratch/bvilasen/ast149/sphere_explosion/output_files/
outdir=/raid/bruno/data/cosmo_sims/cholla_pm/sphere_explosion/
```
Upon completion, you should obtain 11 output files. The initial and final densities and pressures (in code units) of a slice along the y-midplane is shown below.  Examples of how to plot projections and slices can be found in `cholla/python_scripts/Projection_Slice_Tutorial.ipynb`.  
<img src="./images/spherical-overpressure_density_xz.png" alt="Two 2D histograms side by side, showing density of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a circle of density 1 and radius 51.2 centered on (128,128). The remaining cells have a density of 0.1. The rightmost plot is the final density plot at t = 0.10. The location of the circle and slightly around it now has a density value of 0.1. Surrounding this is a 25 cell wide ring of higher density, ranging from 0.2 to 0.4. The edges of the ring are symmetrically perturbed and there is what appears to be a square with pinched, elongated corners overlaid over the whole image with a density of around 0.3. " width="1200" />  

<img src="./images/spherical-overpressure_pressure_xz.png" alt="Two 2D histograms side by side, showing pressure of cells in the z direction vs cells in x direction. The leftmost is the initial density plot with a circle of pressure 11 and radius 51.2 centered on (128,128). The remaining cells have a pressure of 1. The rightmost plot is the final density plot at t = 0.10. The location of the circle and slightly around it now has a pressure value of 1. There is a border around the edges of the plot with a width of 50 cells that has a pressure around 3. The border has beveled edges where the circle used to be and reaches a pressure of 4 in the corners. " width="1200" />  

Currently (8/1/23) this test is producing identical solutions regardless of whether the default hydro or gravity build is used. 
The sphere has exploded, leaving an area of low density and pressure in place of the original higher denisty and pressure sphere. Spherical symmetry is strongly preserved, with the final density having circularly symmetric perturbations ringing the newer area of high density. 
