# HybridStarCFLModel

This folder contains the numerical implementation of hybrid neutron stars using the APR-1 hadronic equation of state and the color–flavor–locked (CFL) quark matter model. The transition point between hadronic and quark matter is determined self-consistently from the thermodynamic equilibrium condition between the two phases.

---

## Files

- apr_cfl_intersections.ipynb  
Determination of the transition pressure between hadronic matter (APR-1) and quark matter by computing the intersection of the pressure curves P_h(μ) and P_q(μ).

- CFL_EOS_builder.ipynb  
Construction of the quark matter equation of state in the CFL model and transformation of the relations P(μ) and ε(μ) into the form ε(P).

- EoS_APR1_CFL.ipynb  
Construction of the hybrid equation of state combining hadronic matter (crust + APR-1) with CFL quark matter through a Maxwell phase transition.

- TOV_Solver.ipynb  
Numerical solution of the Tolman–Oppenheimer–Volkoff equations using a 4th order Runge–Kutta scheme.

- mass_radius_diagram.ipynb  
Computation and visualization of mass–radius relations for hybrid neutron stars.

---

# Methodology

### Determination of the Transition Point

The hadronic phase is described by the APR-1 equation of state.  
From the tabulated quantities (P, ε, n_B), the baryonic chemical potential is computed.

A smooth interpolation of the hadronic pressure P_h(μ) is constructed using **PCHIP interpolation**.

The quark phase is described using the **color–flavor–locked (CFL) model**.  
The transition point is determined from the thermodynamic equilibrium condition

P_h(μ) = P_q(μ)

The solution is obtained numerically by detecting a sign change and applying the **bisection method**.

---

### Construction of the Quark EOS

To solve the TOV equations the relation ε(P) is required.

The quark equation of state is constructed by:

- generating a grid of chemical potential values μ
- computing P(μ) and ε(μ)
- sorting the data with respect to pressure
- applying **PCHIP interpolation**

This produces the final relation

ε_q(P)

---

### Hybrid Equation of State

The hybrid EOS combines:

- **Hadronic phase:** crust + APR-1  
- **Quark phase:** CFL model

The transition is implemented through a **Maxwell construction** at the transition pressure P_tr.

A first-order phase transition is introduced through an energy density discontinuity

ε_q(P_tr) → ε_tr + Δε

Different values of Δε are explored around the critical value predicted by the **Seidov stability criterion**.

---

### TOV Solver

The stellar structure is computed by solving the **Tolman–Oppenheimer–Volkoff equations** using:

- 4th order Runge–Kutta integration
- adaptive step size
- linear interpolation to determine the stellar surface condition P(R) ≈ 0

Central pressures are sampled logarithmically.

---

# Output

The code produces:

- Mass–radius diagrams
- Hybrid star sequences
- Investigation of possible **twin star configurations**
