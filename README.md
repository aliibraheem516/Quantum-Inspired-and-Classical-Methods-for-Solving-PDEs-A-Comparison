
# README: Quantum-Inspired and Classical Solvers for PDEs

## Project Overview

This project explores the development and comparison of **quantum-inspired** and **classical solvers** for solving the **1D viscous Burgers' equation**. The main goal is to evaluate the **efficiency**, **accuracy**, and **scalability** of both types of solvers. Classical solvers include **Baseline Spectral Methods** and **High-Order Split-Operator (HSE) Methods**, while the quantum-inspired solver uses **Quantum Tensor Networks (QTN)** for compression.

The project also includes a **parameter sweep** and **sensitivity analysis**, comparing the performance of the different solvers under various conditions.

### **Note on Quantum Hardware Testing:**
Unfortunately, we were not able to run tests on a real **Quantum Processing Unit (QPU)**. This was due to the unavailability of an open-access QPU at the time of the project. Despite this, quantum simulators were used as substitutes, but true QPU evaluation was not possible.

## Project Structure

- **`step_1_baseline_solver.ipynb`**: Implementation of the classical baseline solver using a spectral method with Fast Fourier Transforms (FFT).
- **`step_2_qtn_mps_solver.ipynb`**: Quantum-inspired Matrix Product State (MPS) based solver for the Burgers' equation, with compression applied.
- **`step_3_hse_split_operator_solver.ipynb`**: High-Order Split-Operator (HSE) solver for the Burgers' equation.
- **`step_4_reporting_and_figures.ipynb`**: Generate figures and compile results into a report format, including CSV and LaTeX outputs.
- **`step_5_parameter_sweep_analysis.ipynb`**: Parameter sweep and sensitivity analysis, including runtime and error comparison of the solvers.
- **`report_exports/`**: Directory for storing all output files (CSV, LaTeX, and figures).
- **`sweep_results/`**: Directory for storing the results of the parameter sweep.

## Steps Breakdown

### Step 1: Baseline Solver Implementation

In this step, we implement a classical **spectral solver** using **FFT** for solving the 1D viscous Burgers' equation.

#### Key Points:
- The **spatial grid** is created using a uniform grid of size \(N_x\).
- The **Fourier Transform** is used to solve the equation in the frequency domain.
- The **nonlinear advection** term and the **linear diffusion** term are handled using a second-order **Runge-Kutta method**.
- The solver returns **snapshots** of the solution at the specified times and the **runtime** for the simulation.

### Step 2: Quantum-Inspired QTN/MPS Solver

In this step, we implement the **Quantum Tensor Network (QTN)** inspired solver using **Matrix Product States (MPS)**. The solution is represented as a tensor network and compressed using **Singular Value Decomposition (SVD)**.

#### Key Points:
- The solution is first computed in the **physical space** using the same method as the baseline solver.
- The **MPS compression** is applied to reduce the **dimensionality** of the solution, leading to a more efficient representation.
- The compression ratio is tracked and stored.

### Step 3: High-Order Split-Operator (HSE) Solver

This step implements the **Strang splitting** method, where the solution is advanced in time by alternating between the **linear diffusion** step and the **nonlinear advection** step.

#### Key Points:
- The **Strang splitting** method is applied to separate the linear and nonlinear parts of the equation.
- The **Fourier** method is used for the linear diffusion, and the **finite difference** method is used for the nonlinear advection.

### Step 4: Reporting and Figure Generation

This step handles the **report generation** using **CSV** files and **LaTeX** for the table output. The results from the solvers are saved to CSV files and used to create figures for comparison.

### Step 5: Parameter Sweep and Sensitivity Analysis

In this step, a **parameter sweep** is conducted to explore the effect of different parameters (e.g., grid size, bond dimension \( \chi \), noise scale) on the performance of the solvers.

#### Key Points:
- The **L2 relative error** and **runtime** are evaluated for different parameter combinations.
- **Figures** are generated to show the sensitivity of the methods to grid size and other parameters.

### Step 6: Final Report Generation

This step generates the **final report**, combining all results into one document.

#### Key Points:
- **Summary statistics** (e.g., error, runtime) for each method are compiled.
- **Figures** and **tables** are saved with high resolution for inclusion in the report.
- A **LaTeX file** is generated for academic-style reporting.

---

### **Submission Requirements** (for GitHub repo):

This repository must include the following:

- **Algorithm Design Brief**: ≤ 5-page PDF describing the chosen framework (QTN, HSE, or hybrid), mapping of PDE (1D Burgers’ Equation), gate decomposition, and resource estimates.
- **Prototype Code**: Open-source implementation runnable on a noiseless simulator and at least one real QPU backend (IBM, IonQ, Rigetti, Quantinuum, etc.).
- **Validation & Benchmark**: Perform a quantitative comparison of the quantum solver against a classical solver reference for the 1-D viscous Burgers shock tube; report L₂-error, wall-clock time, and noisy-simulator metrics (e.g., effective error rates) for ≥ 3 time steps.
- **Resource & Noise Analysis**: Table of qubits, two‑qubit‑gate depth, T‑count (if relevant), and mitigation strategy (e.g. ZNE, Clifford data regression).
- **Quantum Hardware Run**: Execute at least one time step of the 1‑D Burgers benchmark on a physical QPU and present raw and error‑mitigated results, with runtime and noise diagnostics.
- **Scalability Study**: Show how resources scale with grid size.
- **Algorithm Comparison**: Discuss trade‑offs between QTN and HSE.

---

## **Final Notes**

- This project demonstrates the potential of quantum-inspired techniques for solving PDEs and compares their performance with traditional classical methods.
- Quantum-inspired solvers, like **QTN**, could potentially offer **resource-efficient** solutions, especially for large problems.

## **Directory Structure:**

```
/project
    /report_exports        # Final results, CSV files, LaTeX
    /sweep_results         # Results from the parameter sweep
    step_1_baseline_solver.ipynb
    step_2_qtn_mps_solver.ipynb
    step_3_hse_split_operator_solver.ipynb
    step_4_reporting_and_figures.ipynb
    step_5_parameter_sweep_analysis.ipynb
    step_6_final_report.ipynb
```

---

# Running the Project

To run the project, ensure you have the required libraries installed. If you're using a Python environment, you can install the necessary libraries using `pip`:

```bash
pip install numpy matplotlib pandas qiskit
```
