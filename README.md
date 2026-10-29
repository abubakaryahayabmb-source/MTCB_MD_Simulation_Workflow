# Protein–Ligand MD Simulation Workflow with GROMACS & MM/GBSA

A comprehensive teaching guide and practical protocol for executing end-to-end protein–ligand Molecular Dynamics (MD) simulations. This repository covers the complete setup—from initializing a Windows/WSL2 hybrid workstation to CUDA-accelerated GPU execution on Google Colab and final MM/GBSA binding free energy analysis.

---

## 📌 Workflow Overview

| Stage | Platform | Required Tools | Hardware / Acceleration |
|---|---|---|---|
| **1. Preparation** | Windows | UCSF Chimera, SwissParam | CPU |
| **2. Setup & Minimization** | Ubuntu (WSL2) | GROMACS (CPU) | CPU |
| **3. Equilibration & Production** | Google Colab | GROMACS (CUDA build) | **NVIDIA GPU (T4 / L4)** |
| **4. Trajectory Processing** | Ubuntu (WSL2) | GROMACS (CPU) | CPU |
| **5. Binding Free Energy** | Ubuntu (WSL2) | `gmx_MMPBSA` | CPU |

---

## 🚀 Key Features & Highlights

- **WSL2 Environment Configuration:** Complete guide for setting up Ubuntu on Windows with hardware virtualization (VT-x/AMD-V) and troubleshooting common network/DNS issues.
- **System Preparation:** Protocol for force field selection (CHARMM27/TIP3P), ligand parameter generation, solvation, charge neutralization, and energy minimization.
- **GPU-Accelerated Colab Execution:** Automated build scripts for compiling GROMACS with CUDA support on Google Colab GPU runtimes.
- **Fail-Safe MD Production:** Best practices for checkpoint management (`.cpt`), recovering missing trajectories, resuming interrupted sessions without data loss, and concatenating split trajectories (`trjcat`).
- **Post-Simulation Analysis:** Standardized commands for Periodic Boundary Condition (PBC) correction, RMSD, RMSF, Radius of Gyration ($R_g$), Hydrogen Bonding, SASA, and automated Python summary plotting.
- **MM/GBSA Energy Calculations:** Step-by-step installation and execution of `gmx_MMPBSA` for end-state binding free energy estimation.

---

## 📊 Benchmark Reference Timings

Example timing references recorded for a ~61,590 atom system (COX–diclofenac complex):

- **NVT Equilibration (100 ps):** ~94 seconds (~92 ns/day on Google Colab L4 GPU)
- **Production MD (100 ns):** ~14 hours 52 minutes (~161 ns/day on Google Colab L4 GPU)
- **MM/GBSA (201 frames):** ~59 minutes (Intel i7 Dual-Core Laptop)

---

## 📚 References & Resources

1. **GROMACS Documentation:** [manual.gromacs.org](https://manual.gromacs.org)
2. **`gmx_MMPBSA` Documentation:** [valdes-tresanco-ms.github.io/gmx_MMPBSA/](https://valdes-tresanco-ms.github.io/gmx_MMPBSA/)
3. **SwissParam Server:** [swissparam.ch](http://www.swissparam.ch/)
4. Valdés-Tresanco, M.S., et al. *gmx_MMPBSA: A New Tool to Perform End-State Free Energy Calculations with GROMACS.* J. Chem. Theory Comput. 2021, 17(10), 6281–6291.
