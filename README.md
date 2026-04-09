# Sky130-Customized-Cells
Custom standard cell design using Sky130, focused on reducing propagation delay via transistor-level optimization and validated with simulation.

# Propagation Delay
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/0128f6c9-4541-4173-83b4-1db375740633" />
Figure below presents the non-parasitic simulation results of the STANDARD CELL inverter sky130_fd_sc_hd__inv_1. The delay values obtained from the transient simulation are:

- tpHL (Propagation Delay High-to-Low) ≈ 1.03 × 10⁻¹¹ s ≈ 0.0103 ns
- tpLH (Propagation Delay Low-to-High) ≈ 2.05 × 10⁻¹¹ s ≈ 0.0205 ns

These results indicate that the standard cell inverter exhibits an unbalanced delay, where the low-to-high transition is significantly slower than the high-to-low transition. This imbalance may lead to timing issues in digital circuits.
This imbalance can be explained by the use of a high-threshold-voltage (HVT) PMOS transistor in the standard cell. The higher threshold voltage reduces the PMOS drive strength, lead to slower pull-up transition. Moreover, the fixed sizing ratio (Wp = 1000nm, Wn = 650nm) is not flexible, which limits optimization and contributes to the observed delay imbalance.
