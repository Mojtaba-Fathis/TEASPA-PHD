# Quick start

The Windows binary is not published yet. Once a release is available:

1. Download the Windows ZIP from https://github.com/Mojtaba-Fathis/TEASPA-PHD/releases.
2. Compare its SHA-256 hash with the checksum provided with that release.
3. Extract the package and read EULA.txt, DISCLAIMER.txt and THIRD_PARTY_LICENSES.txt.
4. Run TEASPA-PHD_v1.2.0_Beta.exe.
5. Open an exported ETABS .e2k, SAP2000 .s2k/.txt, or MIDAS Gen .mgt model.
6. Review member geometry, units, material properties, loads and hinge parameters.
7. Apply/stage the selected hinges and save a separate patched model.
8. Import the result into the originating analysis program and independently verify properties and assignments.

BRB curves represent nonlinear-static backbones, not validated cyclic material models. SAP2000 BRB export remains disabled. See DISCLAIMER.txt for engineering limitations.
