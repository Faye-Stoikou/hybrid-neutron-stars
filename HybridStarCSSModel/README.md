# HybridStarCSSModel

- EoS_APR1_CSS.ipynb  
Construction of the hybrid equation of state using APR-1 hadronic matter and the Constant Speed of Sound (CSS) quark matter model.

- TOV_solver.ipynb  
Numerical implementation of the Tolman–Oppenheimer–Volkoff equations using a 4th order Runge–Kutta method.

- mass_radius_diagram.ipynb  
Computation of mass–radius relations and visualization of hybrid star configurations.

---

# Methodology

### Equation of State Construction

The equation of state is constructed in different density regimes:

- **Crust:** Three parametrizations describe the low-density region  
- **Hadronic phase:** APR-1 equation of state  
- **Quark phase:** Constant Speed of Sound (CSS) model for transition pressure 'P_tr'

This allows the modeling of a **first-order phase transition** between hadronic and quark matter.

### TOV Solver

The stellar structure is obtained by solving the **Tolman–Oppenheimer–Volkoff equations** using:

- 4th order Runge–Kutta integration
- adaptive step size  
- linear interpolation to determine the stellar surface condition 'P(R) ≈ 0'

Central pressures are sampled logarithmically.

### Parameter Study

The code explores different hybrid star configurations by varying:

- transition pressure 'P_tr'
- energy density discontinuity ΔE around the critical value ΔE_crit determined by the Seidov stability

For each parameter set the **mass–radius relation** is computed.

---

# Output

The code produces:

- Mass–radius diagrams
- Hybrid star sequences
- Exploration of possible **twin star solutions**
