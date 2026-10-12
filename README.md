# Thermochemical model fidelity in hypersonic nose drag, heating and shape

Course project for Fundamentals of Hypersonic Flows (Politecnico di Milano, academic year 2025/26).
The full report is in [report.pdf](report.pdf); the simulation code is not public.

The study asks how much the thermochemical model changes the drag, the stagnation heating and the
heat-constrained optimal shape of a slender axisymmetric forebody at Mach 12 and 45 km. A calorically
perfect gas (SU2) is compared with a two-temperature, five-species non-equilibrium air model (SU2-NEMO
with Mutation++) on a family of smoothly blunted ogives described by a cubic Bézier curve, with nose
radius, fullness and fineness ratio as shape variables.

## Method

- Structured body-conforming grids, with a band adaptation that sharpens the bow shock and leaves the
  wall-normal resolution untouched.
- Perfect-gas stagnation heating within 5.5% of the Fay–Riddell correlation on the fine grid.
- Isothermal wall at 300 K in three catalysis regimes: non-catalytic, finite recombination efficiency
  and super-catalytic.
- Minimum-drag shape optimisation with the stagnation heat flux below a limit, set at the Fay–Riddell
  value (3.26 MW/m²) as a reference rather than a survivability threshold: Kriging surrogates for drag
  and heat flux, a 15-point Latin-hypercube design and 20 infill iterations of constrained expected
  improvement.

## Results

- On the same grid, the non-equilibrium model lowers the stagnation heat flux by about one third
  (2.82 → 1.91 MW/m², −32%), while the drag coefficient barely moves (CD 0.513 against 0.510).
- Catalysis matters little at this condition: the three wall regimes differ by less than 10%, because
  the shock layer is chemically frozen.
- Under the perfect-gas constraint the optimum is a slender body at the upper fineness bound
  (L/D = 3.0, CD ≈ 0.277 against 0.51 for the baseline), with the heat flux on the limit. At that shape
  the non-equilibrium heat flux is 2.51 MW/m², below the limit: the constraint relaxes, so the optimal
  shape depends on the model.

## Author

Marco D'Agostino. Course taught by Prof. Giulio Gori.
