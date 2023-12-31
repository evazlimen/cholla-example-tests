# Cholla Examples
Result of the example tests given in https://github.com/cholla-hydro/cholla.

# Tests which are working as expected:  
1D:
- 123 (Einfeldt Strong Rarefaction)
- Blast
- Constant
- Sod
- Sound wave
- Square wave
- Strong shock
- Test 3
  
2D:
-  Constant
-  Gresho
-  KH discontinuous
-  Noh
-  Sod
-  Sound wave
  
3D:
- Advecting Field Loop
- Alfven Aave
- Brio & Wu
- Circularly Polarized Alfven Wave
- Constant
- Dai and Woodward MHD Shocktube
- Einfeldt Strong Rarefaction MHD 
- Fast Magnetosonic
- Resolution Independent Kelvin-Helmholtz
- MHD Blast
- MHD Contact Wave
- Orszag-Tang Vortex
- Ryu and Jones MHD shock tube 1a
- Ryu and Jones MHD shock tube 4d
- Slow Magnetosonic
- Sod shocktube
- Spherical overpressure
- Uniform
- Sound wave
- Noh

# Tests that require diode boundaries to be disabled:
1D:  
- Shu & Osher shock tube
- Stationary
- Two Shocks

2D:
- Implosion

# Tests not performing as expected (mostly due to issues with initial conditions):
1D:  
- Creasey shock: something with the initial conditions is not being set correctly
- Noh

2D: 
- KH Resolution Independent: initial conditions are not being set correctly
- Rayleigh-Taylor mixing is not occuring
- Disk: appears to be initialized correctly but errors during the run.
  
3D:
- Disk: something with the initial conditions is not being set correctly and the grid is being initialized with zero energy and density
- spherical collapse
- Zeldovich pancake: fails to run with the cosmology build, claims "To run a Zeldovich Pancake COSMOLOGY has to be turned ON"
