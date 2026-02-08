# MIT iQuHack 2026 — Solutions

## Challenge overview (Peak Bitstring Recovery)

**Task:** For each OpenQASM 2 circuit, recover the **peak bitstring** (the computational-basis outcome with maximum amplitude / probability).  
**Note:** The platform accepts the bitstring or its reverse (bit-order agnostic).

### Problem list

| Problem | Name | Qubits | Points | Recommended strategy | Files |
|---:|---|---:|---:|---|---|
| P1 | Little Dimple 🫧 | 4 | 10 | Visual inspection (gate structure) | `Files/P1_little_peak.qasm` |
| P2 | Small Bump 🪨 | 20 | 20 | Full statevector simulation (CPU) | `Files/P2_small_bump.qasm`, `Solutions/P2.ipynb` |
| P3 | Tiny Ripple 🌊 | 30 | 30 | Full statevector simulation + argmax probability | `Files/P3_tiny_ripple.qasm`, `Solutions/P3.ipynb` |
| P4 | Gentle Mound 🌿 | 40 | 40 | MPS simulation (tuned bond/truncation) | `Files/P4_gentle_mound.qasm`, `Solutions/P4.ipynb` |
| P5 | Soft Rise 🌄 | 50 | 50 | Higher bond MPS + multi-run sampling + aggregation | `Files/P5_soft_rise.qasm`, `Solutions/P5.ipynb` |
| P6 | Low Hill ⛰️ | 60 | 60 | Circuit simplification + approximate transpilation | `Files/P6_low_hill.qasm` |
| P7 | Rolling Ridge 🏞️ | 46 | 70 | Decompose via interaction graph; solve subcircuits | `Files/P7_rolling_ridge.qasm` |
| P8 | Bold Peak 🏜️ | 72 | 80 | Decomposition + iterative refinement | `Files/P8_bold_peak.qasm` |
| P9 | Grand Summit 🏔️ | 56 | 90 | Combine simplification + partial sim + decomposition | `Files/P9_grand_summit.qasm` |
| P10 | Eternal Mountain 🗻 | 56 | 100 | Full toolbox: simplification + decomposition + search | `Files/P10_eternal_mountain.qasm` |

---

## Results 

- **P1:** `DONE`  
- **P2:** `DONE`  
- **P3:** `DONE`  
- **P4:** `DONE`  
- **P5:** `DONE`  
- **P6:** `TODO`  
- **P7:** `TODO`  
- **P8:** `TODO`  
- **P9:** `TODO`  
- **P10:** `TODO`


### P1 — Little Dimple 🫧 (4 qubits, 10 pts)
**Strategy:** Visual inspection  
This circuit is intentionally simple. By inspecting the gate sequence and its effect on the computational basis, the peak bitstring can be inferred directly without running a simulator.

**Files**
- QASM: `Files/P1_little_peak.qasm`

---

### P2 — Small Bump 🪨 (20 qubits, 20 pts)
**Strategy:** Full statevector simulation (CPU)  
The circuit size is small enough to allow exact classical simulation. I simulate the full statevector and directly identify the basis state with the maximum probability amplitude.

**Files**
- QASM: `Files/P2_small_bump.qasm`  
- Notebook: `Solutions/P2.ipynb`

---

### P3 — Tiny Ripple 🌊 (30 qubits, 30 pts)
**Strategy:** Full statevector simulation with probability extraction  
Although larger, the circuit remains within feasible limits for classical simulation. I compute the final statevector and extract the dominant outcome by ranking probabilities.

**Files**
- QASM: `Files/P3_tiny_ripple.qasm`  
- Notebook: `Solutions/P3.ipynb`

---

### P4 — Gentle Mound 🌿 (40 qubits, 40 pts)
**Strategy:** Matrix Product State (MPS) simulation  
At this size, full statevector simulation becomes expensive. I switch to an MPS-based simulator with controlled bond dimension and truncation, which efficiently approximates the output distribution and reveals the peak bitstring.

**Files**
- QASM: `Files/P4_gentle_mound.qasm`  
- Notebook: `Solutions/P4.ipynb`

---

### P5 — Soft Rise 🌄 (50 qubits, 50 pts)
**Strategy:** High-bond MPS + repeated sampling and aggregation  
The circuit is highly entangling and can appear nearly uniform under naive simulation. I increase the bond dimension, run multiple sampling passes, and aggregate results to uncover the hidden bias toward the peak bitstring.

**Files**
- QASM: `Files/P5_soft_rise.qasm`  
- Notebook: `Solutions/P5.ipynb`


## Solutions — Recovered Peak Bitstrings

The following peak bitstrings were recovered for the solved challenges.  
(The submission platform accepts each bitstring or its reverse.)

| Problem | Qubits | Peak Bitstring | Notes |
|-------:|-------:|----------------|-------|
| **P1** | 4  | `1001` | Inferred directly from circuit structure |
| **P2** | 20 | `11000001000100011000` | Exact statevector simulation |
| **P3** | 30 | `001110001111101100001101010001` | Exact statevector simulation |
| **P4** | 40 | `1011011000101000010011001110100001010110` | MPS simulation |
| **P5** | 50 | `01101000100100001010101011100000010111100011111110` | High-bond MPS + sampling aggregation |

---

### Additional recovered solutions (not fully documented)

These solutions were recovered during the event but are not yet fully written up in this repository.

**P7 — Rolling Ridge (46 qubits)**  
Peak bitstring:
```
0000011101100100001000111100111111111101000110
```
Estimated probability: `0.36032951062222224`

**P8 — Bold Peak (72 qubits)**  
Peak bitstring:
```
010100010010111001000011110001110011101110100011010001000111101001111101
```

---

**Contributors**
- Joven Sekhon (JSekhon)
- Elena Yu (yxele)



### REQUIREMENTS 

```bash
pip install -r requirements.txt
