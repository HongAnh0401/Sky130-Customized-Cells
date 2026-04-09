# Sky130-Customized-Cells
Custom standard cell design using Sky130, focused on reducing propagation delay via transistor-level optimization and validated with simulation.

# Propagation Delay
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/0128f6c9-4541-4173-83b4-1db375740633" />
Figure below presents the non-parasitic simulation results of the STANDARD CELL inverter sky130_fd_sc_hd__inv_1. The delay values obtained from the transient simulation are:

- tpHL (Propagation Delay High-to-Low) ≈ 1.03 × 10⁻¹¹ s ≈ 0.0103 ns
- tpLH (Propagation Delay Low-to-High) ≈ 2.05 × 10⁻¹¹ s ≈ 0.0205 ns

The results show that the inverter has an unbalanced delay, with the low-to-high transition slower than the high-to-low transition, which may cause timing issues in digital circuits. This behavior is mainly due to the use of an HVT PMOS, which reduces pull-up strength and slows down the transition.
In addition, the fixed sizing ratio (Wp = 1000 nm, Wn = 650 nm) limits optimization and further contributes to the imbalance.
