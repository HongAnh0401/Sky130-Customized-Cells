# Sky130-Customized-Cells
Custom standard cell design using Sky130, focused on reducing propagation delay via transistor-level optimization and validated with simulation.

# Propagation Delay
## Standard Cell
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/0128f6c9-4541-4173-83b4-1db375740633" />
Figure below presents the non-parasitic simulation results of the STANDARD CELL inverter sky130_fd_sc_hd__inv_1. The delay values obtained from the transient simulation are:

- tpHL (Propagation Delay High-to-Low) ≈ 1.03 × 10⁻¹¹ s ≈ 0.0103 ns
- tpLH (Propagation Delay Low-to-High) ≈ 2.05 × 10⁻¹¹ s ≈ 0.0205 ns

The results show that the inverter has an unbalanced delay, with the low-to-high transition slower than the high-to-low transition, which may cause timing issues in digital circuits. This behavior is mainly due to the use of an HVT PMOS sky130_fd_pr__pfet_01v8_hvt, which reduces pull-up strength and slows down the transition.

In addition, the fixed sizing ratio (Wp = 1000 nm, Wn = 650 nm) limits optimization and further contributes to the imbalance.<br><br>
## Custom Cell
<img width="1481" height="570" alt="custom" src="https://github.com/user-attachments/assets/343f1ff8-01e4-489e-a297-7dc633cd2122" />
Figure below shows the non-parasitic simulation results of the CUSTOM CELL inv_1. The extracted delay values are:

- tpHL ≈ 1.23 × 10⁻¹¹ s ≈ 0.0123 ns
- tpLH ≈ 1.25 × 10⁻¹¹ s ≈ 0.0125 ns

These values are very close, indicating that the rising and falling delays are well balanced. This improvement is achieved by properly optimizing the transistor sizing (W/L), particularly the PMOS-to-NMOS width ratio (Wp = 1050nm/Wn = 450nm), during the design process. Also replace the HVT PMOS with the normal one: sky130_fd_pr__pfet_01v8.

Just like inv_1. Here is the consumption of cell NAND2_1, NOR2_1:

- nand2_1:
<img width="818" height="343" alt="image" src="https://github.com/user-attachments/assets/9e8264df-be70-4b36-a665-45b7962d3b04" />
<img width="819" height="148" alt="image" src="https://github.com/user-attachments/assets/bb164082-2751-44ed-b4cf-5769dc87e259" />


Worst-case delay occurs during the transition between 1(A), 0(B) to 1(A), 1(B), where the node is driven by B. This is because pin A and B are connected in series at NMOS area.

- nor2_1
<img width="815" height="339" alt="image" src="https://github.com/user-attachments/assets/65c30b85-feed-4692-b5e2-b75652190df2" />
<img width="811" height="155" alt="image" src="https://github.com/user-attachments/assets/0e69c14a-c0b7-4fe1-b5b5-47fde0b6b605" />
Worst-case delay occurs during the transition between 0(A), 0(B) to 1(A), 0(B), where the node is driven by A. This is because pin A and B are connected in series at PMOS area.

# Layout and characterization
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-56-57" src="https://github.com/user-attachments/assets/de7c2458-1dd4-435d-bfa7-98d89796d85e" />
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-50-30" src="https://github.com/user-attachments/assets/b5b994dc-c3be-4fe3-b7a9-b52940487928" />
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-51-01" src="https://github.com/user-attachments/assets/40682c5b-0d0c-4db7-815f-8d0913034698" />

