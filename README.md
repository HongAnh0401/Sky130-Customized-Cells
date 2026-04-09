# Sky130-Customized-Cells
Custom standard cell design using Sky130, focused on reducing propagation delay via transistor-level optimization and validated with simulation.

# Propagation Delay
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/0128f6c9-4541-4173-83b4-1db375740633" />
Figure below presents the non-parasitic simulation results of the STANDARD CELL inverter sky130_fd_sc_hd__inv_1. The delay values obtained from the transient simulation are:

- tpHL (Propagation Delay High-to-Low) ≈ 1.03 × 10⁻¹¹ s ≈ 0.0103 ns
- tpLH (Propagation Delay Low-to-High) ≈ 2.05 × 10⁻¹¹ s ≈ 0.0205 ns

The results show that the inverter has an unbalanced delay, with the low-to-high transition slower than the high-to-low transition, which may cause timing issues in digital circuits. This behavior is mainly due to the use of an HVT PMOS sky130_fd_pr__pfet_01v8_hvt, which reduces pull-up strength and slows down the transition.

In addition, the fixed sizing ratio (Wp = 1000 nm, Wn = 650 nm) limits optimization and further contributes to the imbalance.


<img width="1481" height="570" alt="custom" src="https://github.com/user-attachments/assets/343f1ff8-01e4-489e-a297-7dc633cd2122" />
Figure below shows the simulation results of the CUSTOM CELL inv_1. The extracted delay values are:

tpHL ≈ 1.23 × 10⁻¹¹ s ≈ 0.0123 ns
tpLH ≈ 1.25 × 10⁻¹¹ s ≈ 0.0125 ns

These values are very close, indicating that the rising and falling delays are well balanced. This improvement is achieved by properly optimizing the transistor sizing (W/L), particularly the PMOS-to-NMOS width ratio (Wp/Wn), during the design process. Also replace the HVT PMOS with the normal one: sky130_fd_pr__pfet_01v8.
