# Structural Simulation

Experimental browser-based finite-element analysis (FEA) for STL geometry, deployed on GitHub Pages.

## Current features
- Interactive STL viewer and placement of supports and forces
- Voxel-derived tetrahedral mesh, isotropic linear-elastic finite elements
- Matrix-free preconditioned conjugate-gradient displacement solution
- Element von Mises stress visualization and maximum displacement
- Adjustable mesh resolution and nodal support/load patch radius
- Element-kernel consistency checks for volume, symmetry, rigid translation and positive stiffness

## Critical limitations
**Not a validated engineering tool. Do not use it to certify load-bearing 3D prints.**

- STL units are assumed to be mm; loads are N, stresses MPa.
- Material is modeled as fully solid and isotropic. Infill %, wall count, print orientation and interlayer adhesion do not affect results.
- Voxelization can erase holes, thin walls, radii and small features.
- Selected surface locations map to spherical patches of mesh nodes, not physically accurate distributed face tractions or screw contact.
- All three displacement components are fixed at support nodes; no friction, preload or contact.
- Local maximum stress is mesh-sensitive and may be singular at supports and loads.
- Solver currently runs on the main browser thread and may become unresponsive at high resolution.
- No fatigue, creep, buckling, plasticity, fracture or safety certification.
- Basic internal kernel checks are not sufficient analytical or experimental validation.

## Next engineering milestones
1. Automated cantilever and patch benchmark tests, including mesh convergence.
2. Global force balance, reaction-force calculation and residual reporting.
3. Robust quality-controlled conforming tetrahedral mesher.
4. True surface loads, support regions and bolt/washer boundary conditions.
5. Web Worker solve with progress and cancellation.
6. Orthotropic, print-orientation-dependent material models backed by coupon measurements.
7. Reproducible simulation files and reports.

## Run
Open the GitHub Pages site. Three.js is loaded via esm.sh and requires internet access. STL files are processed locally in the browser and are not sent to an application backend.
