# Cholla Examples
Result of the example tests given in https://github.com/cholla-hydro/cholla.

# Tests not performing as expected:
1D:  
- Creasey shock: something with the initial conditions is not being set correctly
- Noh
- Trac & Pen: Cholla is potentially failing galilean invariance

3D:
- Disk: something with the initial conditions is not being set correctly and the grid is being initialized with zero energy and density
- Sound wave: density and pressure are being held constant for the duration
- spherical collapse
- Zeldovich pancake: fails to run with the cosmology build, claims "To run a Zeldovich Pancake COSMOLOGY has to be turned ON"
- Noh. also, while Noh runs on main, for 2D and 3D on dev you get "ABORT: noh -> Unknown custom boundary condition."

# Tests that require diode boundaries to be disabled:
1D:  
- Shu & Osher shock tube
- Stationary
- Two Shocks

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

Results of 2D tests coming soon!




