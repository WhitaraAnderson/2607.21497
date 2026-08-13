# PolyChord samples for the Hubble-tension review

“Hubble tension: a short review of theoretical explanations” (arXiv:2607.21497)

This repository contains the PolyChord sample products used for the numerical results in the associated Hubble-tension review. It is a data release, not a complete executable analysis environment: external Boltzmann solvers, likelihood packages, and likelihood data are not included.

## Directory layout

- `EDE/` contains 14 early-dark-energy chain groups.
- `LCDM/` contains 12 flat Lambda-CDM chain groups.
- Each chain group is stored in a directory whose name is the common file prefix.

Each group contains four files:

- `<prefix>.1.txt`: weighted posterior samples in GetDist-compatible text format;
- `<prefix>.input.yaml`: the Cobaya input configuration;
- `<prefix>.updated.yaml`: the fully expanded configuration recorded by Cobaya;
- `<prefix>.logZ`: the PolyChord log-evidence summary.

The first two columns of each sample file are the sample weight and minus log posterior, followed by sampled and derived parameters identified in the header row.

## Numerical software

- The EDE calculations used [AxiCLASS](https://github.com/PoulinV/AxiCLASS), based on CLASS 3.3.0.
- The Lambda-CDM calculations used [CAMB 1.6.6](https://github.com/cmbant/CAMB).
- Sampling was performed with [PolyChordLite](https://github.com/PolyChord/PolyChordLite) through [Cobaya](https://github.com/CobayaSampler/cobaya).

## Reuse and reproducibility

Machine-specific absolute paths have been removed from the public YAML files by replacing them with `path: null`. Users must install the required software and likelihood data locally and provide appropriate paths where necessary.

The YAML files document the model parameters, priors, likelihood combinations, and PolyChord settings used for each chain. The `.1.txt` files are posterior products and are suitable for analysis with [GetDist](https://github.com/cmbant/getdist). They do not contain the complete PolyChord dead-point and live-point history required to reconstruct a nested-sampling run from scratch.

The reported Bayesian evidences should only be compared between runs with compatible model definitions, likelihoods, and prior choices.

## GitHub upload note

Several sample files are larger than GitHub's 25 MiB browser-upload limit, although every file is below the 100 MiB limit for regular Git repositories. Upload this directory with Git or GitHub Desktop rather than the browser file uploader; Git LFS is not required for the current files.
