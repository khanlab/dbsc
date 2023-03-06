## Structural Connectivity Applied To Targeted Regions (SCATTR)
[![Documentation Status](https://readthedocs.org/projects/scattr/badge/?version=stable)](https://scattr.readthedocs.io/en/stable/?badge=stable)
![Version](https://img.shields.io/github/v/tag/khanlab/scattr?label=version)
![Python3](https://img.shields.io/badge/python-3.8_|_3.9_|_3.10-blue.svg)
[![Tests](https://github.com/khanlab/scattr/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/khanlab/scattr/actions/workflows/test.yml?query=branch%3Amain)
![Docker Pulls](https://img.shields.io/docker/pulls/khanlab/scattr)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7636506.svg)](https://doi.org/10.5281/zenodo.7636506)

SCATTR is a BIDS App that performs tractography to identify
connections between subcortical structures (i.e. map the subcortical
connectome), making use of existing neuroimaging tools like `prepdwi`,
`Freesurfer`, and `Mrtrix3`.

This workflow was used to process the data for the analysis from
[`hcp_subcortical_repo`](https://github.com/kaitj/hcp_subcortical_repro).

### Contributing
Clone the git repository. SCATTR dependencies are managed with Poetry
(version 1.2.x), which you'll need installed on your machine.
You can find instructions on the Poetry
[website](https://python-poetry.org/docs/).

Then, setup the development environment with the following commands:

```
poetry install
poetry run poe setup
```

SCATTR uses poethepoet as a task runner.
You can see what commands are available by running:

```
poetry run poe
```

If you wish, you can also run poe [command] directly by installing poethepoet
on your system. Follow the install instructions at the link above.

SCATTR uses pre-commit hooks (installed via the poe setup command above) to lint
and format code (we use black, isort, flake8). By default, these hooks are
run on every commit.

Please be sure they all pass before making a PR.

### Notes

* Original workflow had worked on HCP data which had transforms readily
available. Transforms need to be computed to standard spaces used
(MNI2009b is sufficient).
* Current workflow assumes dwi data has been preprocessed and `Freesurfer` has
already been run. Future implementation will include option to run missing
steps.
* Original workflow was run using scripts similar to those in
`resources/example_scripts`

### Relevant Papers

* Kai, J., Khan, A.R., Haast, R.A.M., Lau, J.C. (2022).
Mapping the subcortical connectome using in vivo diffusion MRI: feasibility
and reliability. Terra incognita: diving into the human subcortex,
special issue of NeuroImage.
doi: [10.1016/j.neuroimage.2022.119553](https://doi.org/10.1016/j.neuroimage.2022.119553).
