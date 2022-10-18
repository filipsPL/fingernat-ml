# Structural Interactions Fingerprints (SIFs) for ML - a complete pipeline

Directory with code, docking data and prepared SIFs outputs for ML.

## Data structure

* `1-rna_targets/` - RNA targets used for molecular docking; 3 pdb files were used for each target, except for HIV with 4 pdb files.
* `2-docking-results/` - rDock results - docked ligands (250 poses each) to their RNA targets, not uploaded due to file size restrictions.
* `3-best-poses/` - cut 3 best poses (with lowest docking scores) for each ligand docked to each target.
* `4-SIFs/` - SIFs for each set of docked ligands - target complex.
  * `all/` - SIFs calculated for each set of docked ligands - target complex; figeRNAt direct output.
  * `1best/` - SIFs for 1. best pose of each ligand, cut from appropriate  SIFs results from `all/`.
  * `3best/` - mean of SIFs for 3 best poses of each ligand, calculated based on appropriate SIFs results from `all/`.
* `5-SIFs_merged/` - SIFs merged for all pdbs from each target (pasted side by side) with added information about each ligand's activity. **FINAL RESULTS FOR ML.**
  - weka (`*.arff`) files (converted from tsv's)
  - weka (`*__zerosRemoved.arff`) files with removed columns that contain only zeros


---

* `jupyter_notebooks/`
  * `Preprocessing.ipynb` - jupyter notebook with code to cut 3 best poses of each ligand from rDock results -> generates directory `3-best-poses/`
  * `Calculate_SIFs.ipynb` - jupyter notebook with code to calculate SIFs, merge them and add ligands' activity information -> generates directories `4-SIFs/` & `5-SIFs_merged/`
