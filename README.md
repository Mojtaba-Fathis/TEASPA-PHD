# TEASPA-PHD (TEASPA Plastic Hinge Designer)

**Version 1.2.0 Beta** — [Download the Windows pre-release](https://github.com/Mojtaba-Fathis/TEASPA-PHD/releases/tag/v1.2.0-beta)  
*Experimentally Calibrated Nonlinear Plastic Hinge Formulation & Automation Engine*  
Supported Platforms: **ETABS (`.e2k`)** | **SAP2000 (`.s2k`, `.txt`)** | **MIDAS Gen (`.mgt`)**

---

## Overview

**TEASPA-PHD** is a specialized structural earthquake engineering desktop tool designed to calculate, visualize, and automatically assign nonlinear plastic hinge properties directly into structural analysis models. 

By integrating experimentally calibrated backbone formulations from Taiwan's latest pushover assessment guidelines (**TEASPA V5.0**, NCREE-25-002) and recent peer-reviewed publications, TEASPA-PHD bridges the gap between empirical laboratory research and practical structural modeling in **ETABS**, **SAP2000**, and **MIDAS Gen**.

![TEASPA-PHD Logo](assets/App_logo.png)

---

## Key Features

- **Multi-Platform Support**: Direct text model round-tripping for:
  - **ETABS**: `.e2k` text files (ETABS 18 through 23+).
  - **SAP2000**: `.s2k` and `.txt` text files.
  - **MIDAS Gen**: `.mgt` text files with automatic section & ASTM/AISC material database resolution.
- **Comprehensive Nonlinear Hinge Models**:
  - **Steel Beams**: Welded Flange-Bolted Web (WFBW), Cover-Plate Connection (CPC), and Reduced Beam Section (RBS) moment hinges.
  - **Hollow Structural Sections (HSS / Box Columns)**: Axial-force dependent flexural hinge formulations with direct axial load ($P$) or axial ratio ($P/P_{ye}$) input.
  - **Square Concrete-Filled Steel Tube (CFST) Columns**: Advanced flexural-axial plastic hinge model accounting for steel tube confinement and composite interaction (*Lin, Huang, Fathisepahvand et al., 2026*).
  - **Conventional H-Shaped Steel Braces**: Axial tension and compression buckling hinges with localized AISC-calibrated post-buckling degradation and convergence-adjusted options.
  - **Buckling-Restrained Braces (BRB)**: Generalized ASCE/SEI 41-23 Chapter 9 & ANSI/AISC 342-22 nonlinear-static core backbone formulation.
- **Interactive Visual Feedback**:
  - Live Matplotlib backbone curve plotting with labeled characteristic points (Yield, Peak, Residual, Failure).
  - Normalization mode toggle: **TEASPA V5.0** (standardized deformation offsets) vs. **Legacy TEASPA**.
  - Dynamic source-unit preservation (kN, N, kips, mm, cm, m, in, ft).
- **Batch Processing & Automated Patching**:
  - Assign hinges individually or batch-apply to all qualifying frame members.
  - Generates patched `.e2k`, `.s2k`, or `.mgt` files with complete hinge property definitions and frame member assignments.
  - Non-destructive workflow: leaves unaffected elements and solver definitions completely untouched.

---

## System Requirements

- **Operating System**: Microsoft Windows 10 or Windows 11 (64-bit).
- **Prerequisites**: None. The distributed executable is completely self-contained (no Python installation or third-party runtime required).
- **Target Analysis Software**: ETABS (v18+), SAP2000 (v20+), or MIDAS Gen (2022+).

---

> **Release status:** [Version 1.2.0 Beta is available for Windows x64](https://github.com/Mojtaba-Fathis/TEASPA-PHD/releases/tag/v1.2.0-beta). Download the ZIP and SHA256SUMS.txt from the release assets and verify the checksum before extracting. This repository contains distribution documentation and assets; application source code is not included.

## Installation and Execution

1. Download the latest release package (`TEASPA-PHD_v1.2.0_Beta_Windows_x64.zip`) from the [Releases](https://github.com/Mojtaba-Fathis/TEASPA-PHD/releases) page.
2. Extract the ZIP archive to a folder of your choice on your local drive (e.g., `C:\Engineering\TEASPA-PHD`).
3. Run `TEASPA-PHD_v1.2.0_Beta.exe`.
4. (Optional) Create a desktop shortcut to `TEASPA-PHD_v1.2.0_Beta.exe` for convenient access.

---

## Quick Start Workflow

1. **Export Text Model**:
   - In ETABS: `File → Export → ETABS .e2k Text File...`
   - In SAP2000: `File → Export → SAP2000 .s2k Text File...`
   - In MIDAS Gen: `Tools → MGT Command Shell` or export `.mgt`.
2. **Open in TEASPA-PHD**:
   - Click **Open Model...** and select your exported `.e2k`, `.s2k`, or `.mgt` file.
   - The member tree and overview table will populate with all detected frame elements.
3. **Review & Configure Hinges**:
   - Select a frame member from the tree or table.
   - Select the desired hinge formulation (e.g., WFBW Beam, Square CFST Column, BRB).
   - Review material properties, unbraced lengths ($L_b$), and column axial load ratios ($P/P_{ye}$).
   - Inspect the interactive backbone plot and numerical coordinate values ($A, B, C, D, E, IO, LS, CP$).
4. **Stage & Save Patched Model**:
   - Click **Stage This Member** or **Stage All Members**.
   - Click **Save Patched Model...** (or press `Ctrl+Shift+S`) to export the modified structural file.
5. **Import & Analyze**:
   - Open your structural analysis software and import the patched text file.
   - Verify assigned hinge locations and properties before analysis. The BRB model is intended for nonlinear-static/pushover use; calibrated cyclic or nonlinear-dynamic BRB behavior is not established. SAP2000 BRB export remains disabled.

---

## Academic Methodology and Technical Citations

If you use TEASPA-PHD in your research, dissertations, or technical papers, please cite the following foundational publications:

1. **Primary TEASPA Methodology**:  
   Lin, M.-L., Chiou, T.-C., Chung, L.-L., et al. (2025).  
   *Technical Handbook for Taiwan Earthquake Assessment and Strengthening of Structures by Pushover Analysis (TEASPA V5.0)*.  
   National Center for Research on Earthquake Engineering (NCREE), Report No. NCREE-25-002, Taipei, Taiwan.

2. **Steel Hinge Experimental Calibration**:  
   Fathisepahvand, M., Huang, C.-H., Lin, M.-L., et al. (2026).  
   *Experimentally calibrated nonlinear hinge models for steel moment-resisting and concentrically braced frame systems*.  
   Advances in Structural Engineering, 0(0). [doi:10.1177/13694332261463513](https://doi.org/10.1177/13694332261463513)

3. **CFST Column Nonlinear Hinge Methodology**:  
   Lin, M.-L., Huang, C.-H., Fathisepahvand, M., Weng, Y.-T., Chiou, T.-C., Chung, L.-L., Chou, T.-K., and Tseng, Y.-C. (2026).  
   *Nonlinear Hinge Models for Seismic Performance Evaluation of Concrete-Filled Steel Tubular Structures*.  
   Journal of the Chinese Institute of Engineers (JCIE). [doi:10.1080/02533839.2026.2650112](https://doi.org/10.1080/02533839.2026.2650112)

4. **BRB Formulation Standards**:  
   ASCE/SEI 41-23 (2023). *Seismic Evaluation and Retrofit of Existing Buildings*. ASCE, Reston, VA.  
   ANSI/AISC 342-22 (2022). *Seismic Provisions for Evaluation and Retrofit of Existing Structural Steel Buildings*. AISC, Chicago, IL.

---

## Licensing and Terms of Use

- **License Model**: Proprietary, Free for Academic, Educational, and Non-Commercial Research & Evaluation.
- **Redistribution**: Unauthorized public redistribution, cloud re-hosting, or sublicensing is prohibited.
- **Commercial Use**: Use for commercial design, paid engineering consulting, or fee-earning projects requires prior written authorization from the authors.
- **Source Code**: Source code is proprietary and private. Decompilation, reverse engineering, and modification of the compiled binary are prohibited to the maximum extent permitted by applicable law.
- Please review `EULA.txt` and `COPYRIGHT.txt` for complete terms.

---

## Engineering Disclaimer

**TEASPA-PHD is an engineering-assistance and research software tool.**  
All calculated hinge properties, backbone curves, deformation parameters, and patched analysis models must be independently verified by a licensed Professional Engineer (PE / SE) prior to any engineering implementation. The developers and affiliated institutions disclaim all liability for any structural failures, construction defects, or damages resulting from the use of this software.  
See `DISCLAIMER.txt` for the full liability disclaimer.

---

## Authors & Collaborators

- **Mojtaba Fathisepahvand** (Lead Software Developer & Researcher)
- **Min-Lang Lin** (Research Specialist, NCREE)
- **Chao-Hsun Huang** (Associate Professor, Department of Civil Engineering, NTUT)
- **Tsung-Chih Chiou** (Research Specialist, NCREE)
- **Lap-Loi Chung** (Research Specialist, NCREE)
- **Te-Kuang Chou** (Research Specialist, NCREE)
- **Kuan-Hsun Chung** (Research Specialist, NCREE)
- **Yuan-Tao Weng** (Research Specialist, NCREE)

**Affiliations**:
- Department of Civil Engineering, National Taipei University of Technology (NTUT), Taipei, Taiwan.
- National Center for Research on Earthquake Engineering (NCREE), NARLabs, Taipei, Taiwan.

