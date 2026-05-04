# Neural Sensitivity Geometry

Code accompanying the paper:

**Beyond Activation Alignment: The Geometry of Neural Sensitivity**  
Amirhossein Yavari and Farnaz Zamani Esfahlani

This repository contains the main code for computing dataset-level neural sensitivity summaries, S-RAS comparisons, diagnostic probes, robust-training analyses, and Allen Brain Observatory static-gratings analyses.

<p align="center">
  <img src="assets/neural_sensitivity_overview.png" alt="Neural sensitivity overview" width="850"/>
</p>
## Overview

Activation-alignment methods compare representations through stimulus-evoked activity patterns. This project compares representations through dataset-level local sensitivity summaries: expected projected pullback/Fisher operators over specified perturbation families.

The repository includes notebooks/scripts for:

- layer-matching sanity checks and pointwise local-geometry controls;
- class-conditional diagnostic probes;
- robust-training comparisons;
- Allen Brain Observatory static-gratings preprocessing and analysis;
- model training for the computational experiments.

Final manuscript figure assembly/design scripts are not included.

## Repository structure

```text
computational_experiments/
  layer_matching/
  diagnostic_probes/
  robust_training/

biology_allen_static_gratings/
  preprocessing/
  analysis/

training/
  tiny10/
  resnet_vit/
  robust_resnet/

assets/
  neural_sensitivity_overview.png