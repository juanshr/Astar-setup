# A-type star setup
These are the models used in [Hidalgo et al. (2024)](https://ui.adsabs.harvard.edu/abs/2024A%26A...691A.326H/abstract), 
which are based on the fully convective 
star-in-a-box setups (see [Dobler et al. 2006](https://ui.adsabs.harvard.edu/abs/2006ApJ...638..336D/abstract) 
and [Käpylä 2021](https://ui.adsabs.harvard.edu/abs/2021A&A...651A..66K/abstract)) developed for [The Pencil Code](https://pencil-code.nordita.org/).

The current models correspond to a $$2.2 M_\odot$$ A0 star, with a convective core that encompasses 20% of the
radial extent, surrounded by a thick radiative envelope. In [Hidalgo et al. (2024)](https://ui.adsabs.harvard.edu/abs/2024A%26A...691A.326H/abstract),
two *entire star* setups were defined, where their main difference is the radial profile used for the diffusivities. 
Furthermore, a zoom model was presented, where 50% of the radius was retained, increasing the grid points 
available to resolve convection inside the core.  


The full star setups, the so-called MHD and MHD\* groups, are contained in the folders 'MHD\_run' and 'MHDI\_run', respectively,
and the zoom setup is in 'zMHD\_run'.

## Physical description of the model
In each run, the following non-ideal fully compressible MHD equation set is solved: 

$$
\begin{align}
    \frac{\partial \mathbf{A}}{\partial t} &= \mathbf{U} \times \mathbf{B} - \eta \mu_0 \mathbf{J}, \\\
    \frac{D \ln \rho}{D t} &= - \mathbf{\nabla} \mathbf{\cdot} \mathbf{U}, \\\
    \frac{D \mathbf{U}}{D t} &= - \mathbf{\nabla} \Phi - \frac{1}{\rho} \left( \mathbf{\nabla} p - \mathbf{\nabla} \mathbf{\cdot}2 \nu \rho \mathbf{S} + \mathbf{J} \times \mathbf{B} \right)- 2 \mathbf{\Omega}\times \mathbf{U} + \mathbf{f}_d, \\\
    T \frac{Ds}{Dt} &= - \frac{1}{\rho} \left[ \mathbf{\nabla} \mathbf{\cdot} (\mathbf{F}_\text{rad} + \mathbf{F}_\text{SGS})  + \mathcal{H} - \mathcal{C} + \mu_0 \eta \mathbf{J}^2 \right] + 2 \nu \mathbf{S}^2, 
\end{align}
$$

where $$\mathbf{A}$$ is the magnetic vector potential, $$\mathbf{U}$$ is the flow
velocity, $$\mathbf{B} = \mathbf{\nabla} \times \mathbf{A}$$ is the magnetic field,
$$\eta$$ is the magnetic diffusivity, $$\mu_0$$ is the magnetic
permeability of vacuum, $$\mathbf{J} = \mathbf{\nabla} \times \mathbf{B}/\mu_0$$ is
the current density given by Ampère's law, $$D/Dt = \partial/\partial t + \mathbf{U} \mathbf{\cdot}\mathbf{\nabla}$$ 
is the advective derivative, $$\rho$$ is the mass density, $$p$$ is the pressure, $$\Phi$$ is
the fixed gravitational potential, given by the Pad\'e approximation obtained from 1D stellar structure model.
$$\nu$$ is the kinematic viscosity, $$\mathbf{S}$$ is the traceless
rate-of-strain tensor, given by

$$
\displaylines{
S_{ij} = \frac{1}{2}(\partial_j U_i + \partial_i U_j) - \frac{1}{3}\delta_{ij} \mathbf{\nabla} \mathbf{\cdot} \mathbf{U},
}
$$

where $$\delta_{ij}$$ is the Kronecker
delta. $$\mathbf{\Omega}=(0,0,\Omega_0)$$ is the rotation vector and
$$\mathbf{f}_\mathrm{d}$$ describes damping of flows
exterior to the star. $$T$$ is the temperature, $$s$$ is
the
specific entropy, $$\mathbf{F}_\mathrm{rad}$$ is the radiative flux and
$$\mathbf{F}_\mathrm{SGS}$$ is the subgrid-scale (SGS) entropy
flux. The radiative energy flux is given by

$$
\displaylines{
\mathbf{F}_\mathrm{rad} = - K \mathbf{\nabla} T,
}
$$

where $$K$$ is the radiative heat conductivity, a quantity that is
assumed to be constant. $$\mathcal{H}$$ and
$$\mathcal{C}$$ describe additional heating and cooling, respectively,
and we adopted similar expressions as in [Dobler et al. (2006)](https://ui.adsabs.harvard.edu/abs/2006ApJ...638..336D/abstract)
and [Käpylä (2021)](https://ui.adsabs.harvard.edu/abs/2021A&A...651A..66K/abstract)).
The ideal gas equation of state $$p = \mathcal{R}\rho
T$$ is assumed, where $$\mathcal{R}=c_\mathrm{P}-c_\mathrm{V}$$ is the ideal gas constant, 
and $c_\mathrm{P}$ and $c_\mathrm{V}$ are the heat capacities at constant pressure and volume, respectively.


