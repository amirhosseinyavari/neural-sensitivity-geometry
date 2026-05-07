# Neural Sensitivity Geometry

Code accompanying the paper:

**Beyond Activation Alignment: The Geometry of Neural Sensitivity**  
Amirhossein Yavari and Farnaz Zamani Esfahlani

[![arXiv](https://img.shields.io/badge/arXiv-2605.03222-b31b1b.svg)](https://arxiv.org/abs/2605.03222)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

This repository contains the main analysis and training code for the paper
[*Beyond Activation Alignment: The Geometry of Neural Sensitivity*](https://arxiv.org/abs/2605.03222).

The project computes dataset-level neural sensitivity summaries, Spectral Riemannian
Alignment Score (S-RAS) comparisons, diagnostic probes, robust-training analyses,
and Allen Brain Observatory static-gratings analyses.

![Neural sensitivity overview](./assets/neural_sensitivity_overview.png)

## Overview

Activation-alignment methods compare representations through stimulus-evoked
activity patterns. This project compares representations through dataset-level
local sensitivity summaries: expected projected pullback/Fisher operators over
specified perturbation families.

The repository includes notebooks for:

- layer-matching sanity checks and pointwise local-geometry controls;
- class-conditional diagnostic probes;
- robust-training comparisons;
- Allen Brain Observatory static-gratings preprocessing and analysis;
- model training for the computational experiments.

The repository is intended to document and reproduce the main computational
analyses reported in the paper. It is not packaged as a general-purpose library.

## Paper

- arXiv: [2605.03222](https://arxiv.org/abs/2605.03222)
- PDF: [https://arxiv.org/pdf/2605.03222](https://arxiv.org/pdf/2605.03222)
- DOI: [10.48550/arXiv.2605.03222](https://doi.org/10.48550/arXiv.2605.03222)

## Repository structure

```text
assets/
  neural_sensitivity_overview.png

Computational Results/
  Experiments/
    architecture_diagnostic_probes_final.ipynb
    layer_matching_sanity_check_final.ipynb
    robust_vs_standard_experiment_final.ipynb
  Training/
    Cifar_training_Resnet_ViT.ipynb
    robust_resnet_training_cifar.ipynb
    Tiny10_Cifar10_Training.ipynb

Mice Results/
  allen_grating_preprocessing.ipynb
  allen_grating_analysis.ipynb
```

## Main paper mapping

| Paper item | Code location |
|---|---|
| Table 1, layer matching | `Computational Results/Experiments/layer_matching_sanity_check_final.ipynb` |
| Figure 2, diagnostic probes | `Computational Results/Experiments/architecture_diagnostic_probes_final.ipynb` |
| Figure 3, robust training | `Computational Results/Experiments/robust_vs_standard_experiment_final.ipynb` |
| Figure 4 and Table 2, Allen static gratings | `Mice Results/allen_grating_preprocessing.ipynb`, `Mice Results/allen_grating_analysis.ipynb` |
| Model training | `Computational Results/Training/` |

## Data and checkpoints

The computational experiments use CIFAR-10. The biological analyses use the
Allen Brain Observatory Visual Coding dataset, specifically the static-gratings
stimulus condition used in the paper.

Large trained checkpoints, raw datasets, and intermediate analysis outputs are
not included in this repository. The notebooks specify the expected directory
structure and data locations.

To reproduce the reported analyses, you will need to either:

1. train the computational model banks using the notebooks in
   `Computational Results/Training/`, or
2. adapt the loading paths in the analysis notebooks to point to your own
   compatible checkpoints and cached outputs.

Allen Brain Observatory data should be downloaded through AllenSDK-compatible
interfaces or through the Allen Brain Observatory data-access tools.

## Environment

Most computational notebooks were run with Python 3.13. The Allen Brain
Observatory preprocessing notebook was run with Python 3.11 because of AllenSDK
compatibility.

Recommended packages for the computational experiments:

```bash
python >= 3.13
jax
flax
optax
numpy
scipy
scikit-learn
pandas
matplotlib
tqdm
```

Recommended packages for Allen preprocessing and analysis:

```bash
python == 3.11
allensdk
numpy
scipy
scikit-learn
pandas
matplotlib
tqdm
```

Third-party packages are used as external dependencies and are not included in
this repository.

## Usage

A typical workflow is:

1. Train or load model banks using notebooks in `Computational Results/Training/`.
2. Run the layer-matching analysis in
   `Computational Results/Experiments/layer_matching_sanity_check_final.ipynb`.
3. Run the diagnostic-probe analysis in
   `Computational Results/Experiments/architecture_diagnostic_probes_final.ipynb`.
4. Run the robust-training comparison in
   `Computational Results/Experiments/robust_vs_standard_experiment_final.ipynb`.
5. Run Allen preprocessing and analysis using the notebooks in `Mice Results/`.

Because some notebooks depend on cached model outputs or intermediate biological
analysis files, you may need to edit path constants near the top of each notebook
before running it in a new environment.

## Reproducibility notes

- The notebooks contain the main code used to generate the reported experimental
  results.
- Some notebooks include optional configurations beyond the main reported
  experiments.
- Unless otherwise stated, the paper reports CIFAR-10 computational experiments
  and Allen Brain Observatory static-gratings biological analyses.
- Final manuscript figure assembly and design scripts are not included.
- Large checkpoints, raw datasets, and intermediate outputs are intentionally
  excluded from the repository.

## Citation

If you use this code or build on the paper, please cite:

```bibtex
@misc{yavari2026beyondactivationalignment,
  title         = {Beyond Activation Alignment: The Geometry of Neural Sensitivity},
  author        = {Yavari, Amirhossein and Zamani Esfahlani, Farnaz},
  year          = {2026},
  eprint        = {2605.03222},
  archivePrefix = {arXiv},
  primaryClass  = {cs.LG},
  doi           = {10.48550/arXiv.2605.03222},
  url           = {https://arxiv.org/abs/2605.03222}
}
```

## License

This repository is released under the MIT License. 