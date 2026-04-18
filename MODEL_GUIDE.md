# MODEL_GUIDE.md

## Project: Emergent Relational Time (Simulated)

This repository contains the implementation of a minimal model for **emergent relational time**, based on quantum dynamics within a **star-topology graph**.

The model investigates how an **arrow of time** can emerge from local irreversibility (post-selection) inside a system governed globally by unitary evolution.

---

## 1. System Architecture

The simulation uses a **star topology** quantum configuration:

* **Central Qubit (`q0`)** Acts as the correlation hub.
* **Peripheral Qubits (`q1 ... qN-1`)** Form the entanglement register and interact only with the central qubit.
* **Interaction Type** Pairwise `ZZ` couplings between the center and each peripheral node.

### Hamiltonian

$$H = \sum_{i=1}^{N-1} J Z_0 Z_i$$

Where:

* `J` = coupling strength
* `Z0 Zi` = Pauli-Z interaction between center and node `i`

---

## 2. Requirements

```bash
pip install qiskit qiskit-aer matplotlib numpy
```

Recommended:

* Python 3.10+
* Virtual environment

---

## 3. Running the Simulation

Main entry point:

```bash
python run_simulation.py --steps 50 --qubits 5
```

### Configuration

Edit parameters in `config.py`

Typical values:

* `N` = number of qubits
* `T` = total evolution time
* `J` = coupling constant
* `shots` = simulator samples

---

## 4. Core Protocol

The simulation performs a Loschmidt echo style experiment:

1. Initialize an N-qubit quantum state.
2. Apply forward evolution: $U(T)=e^{-iHT}$
3. Apply disturbance operator `W` on a selected qubit.
4. Measure return fidelity and correlations.
5. Apply post-selection for effective irreversibility.

---

## 5. Reading Results

### Echo Decay (Scrambling)

Loschmidt echo:

$$\mathcal{E}(T)$$

Rapid decrease may indicate:

* information dispersal from `q0`
* spreading correlations
* scrambling dynamics

### Emergence of Time Asymmetry

After post-selection:

$$\langle Z_0 Z_i \rangle$$

Broken forward/backward symmetry may indicate:

* local arrow of time
* relational ordering of events
* emergence of a measurable “now”

---

## 6. Conceptual Interpretation

### Time Is Emergent

Time may arise from:

* coarse-graining
* information loss
* subsystem observation

### Global Unitarity Remains Intact

The total isolated system evolves reversibly.

### Local Irreversibility Is Effective

Subsystem observers detect directionality due to projection / trace-out effects.

### Nonlocal Structure

Central mediation through `q0` models hidden connectivity.

---

## 7. Suggested Extensions

* Add Qiskit Aer noise models
* Measure entropy and mutual information
* Test alternative graph topologies
* Interpret graph edges as pre-geometric relations

---

## 8. Optimization Ideas

* Use `SparsePauliOp`
* Higher transpiler optimization levels
* Parallel parameter sweeps
* GPU Aer backend
* JAX / NumPy acceleration

---

## 9. Research Direction

Possible framework:

* time = emergent ordering
* space = correlation geometry
* causality = stable information flow
* reality = relational quantum network

---

## 10. Final Note

You are not simulating clocks.

You are simulating conditions under which clocks become meaningful. ⚛️
