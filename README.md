# Structural Connectivity Applied To Targeted Regions (SCATTR)
[![Documentation Status](https://readthedocs.org/projects/scattr/badge/?version=stable)](https://scattr.readthedocs.io/en/stable/?badge=stable)
![Version](https://img.shields.io/github/v/tag/khanlab/scattr?label=version)
![Python3](https://img.shields.io/badge/python-3.8_|_3.9_|_3.10-blue.svg)
[![Tests](https://github.com/khanlab/scattr/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/khanlab/scattr/actions/workflows/test.yml?query=branch%3Amain)
![Docker Pulls](https://img.shields.io/docker/pulls/khanlab/scattr)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7636506.svg)](https://doi.org/10.5281/zenodo.7636506)

SCATTR is a BIDS App that performs a tractography processing workflow to 
identify connections between targetted structures of interest (extracted from
various atlases) in the brain, using some common neuroimaging tools like 
`prepdwi`, `Freesurfer`, and `Mrtrix3`.

![Example outputs](https://raw.githubusercontent.com/khanlab/scattr/main/docs/images/ex_output.png)

This is useful for:

* Analyzing structural connections of known brain circuits
* Examining specific connections of interest
* Comparison across different groups (e.g. controls vs patients)


## Example use of workflow 
This workflow was used to process and analyze the the data for the from
[`hcp_subcortical_repo`](https://github.com/kaitj/hcp_subcortical_repro) 
(see Kai et al., 2022). 

## Workflow 
A brief summary of the workflow can be found below (see documentation for
a detailed summary):

_Note: The workflow assumes Freesurfer has already been run on the dataset, as 
well as diffusion preprocessing (e.g. distortion correction)._

![Workflow example](https://raw.githubusercontent.com/khanlab/scattr/main/docs/images/workflow.png)

1. Merge the segmentations of structures in a standard template space from 
various sources (if necessary) via 
[labelmerge](https://zenodo.org/record/7636410), which is used downstream to
identify targetted connections.
1. Estimate and apply transformations from standard template space to 
subject-specific space.
1. Further process the pre-processed diffusion data to enable tractography
(e.g. compute response functions, fibre orientation distribution, 
normalization).
1. Perform whole-brain tractography from computed files, applying filtering 
(e.g. SIFT2) to computed tractogram. Once filtered, connections between the 
merged segmentations (from step 1) are identified, generating a connectome map.
1. Analysis can then be performed on the map to examine and explore the 
connectome of interest.

### **Full documentation:** [here](https://scattr.readthedocs.io/en/stable/)

## Relevant Papers

* Kai, J., Khan, A.R., Haast, R.A.M., Lau, J.C. (2022).
Mapping the subcortical connectome using in vivo diffusion MRI: feasibility
and reliability. Terra incognita: diving into the human subcortex,
special issue of NeuroImage. doi: 
[10.1016/j.neuroimage.2022.119553](https://doi.org/10.1016/j.neuroimage.2022.119553).
