# Data Sources — Arms Exports Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Arms Exports: End-Use Enforcement Impossibility) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_conflict_casualties`

100K+ conflict deaths/yr enabled by weapons. Sources: SIPRI, UCDP, UNHCR.

*Full citations: paper §4 (available SSRN).*

### `C2_humanitarian_crisis`

Refugee flows, famine, infrastructure destruction. Sources: UNHCR, OCHA, MSF.

*Full citations: paper §4 (available SSRN).*

### `C3_arms_race_dynamics`

Regional arms races, proliferation. Sources: SIPRI, IISS Military Balance.

*Full citations: paper §4 (available SSRN).*

### `C4_development_diversion`

Military spending crowds out health/education. Sources: World Bank, SIPRI.

*Full citations: paper §4 (available SSRN).*

### `C5_end_use_enforcement_failure`

Diversion, re-transfer, monitoring failure. Sources: ATT, Conflict Armament Research.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $29.6B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Arms Exports (End-Use Enforcement Impossibility)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
