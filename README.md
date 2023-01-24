# COSIMA 2023 Hackathon

See https://github.com/COSIMA/cosima-recipes/issues/191

```
mamba env create -f environment_2022.10.2.yml
conda activate dask-2022.10.2
python -m ipykernel install --user --name dask-2022.10.2 --display-name "Python (dask-2022.10.2)"

conda deactivate
mamba env create -f environment_2022.11.0.yml
conda activate dask-2022.11.0
python -m ipykernel install --user --name dask-2022.11.0 --display-name "Python (dask-2022.11.0)"
```

The notebook in this directory is a stripped-back, edited version of [Decomposing_kinetic_energy_into_mean_and_transient.ipynb](https://github.com/COSIMA/cosima-recipes/blob/eb988580e9867a325bc13e03c540950e41121194/DocumentedExamples/Decomposing_kinetic_energy_into_mean_and_transient.ipynb). The main changes are:
 - Only load data from 2028 onwards. Data prior to this are on a different domain. Xarray silently contenates these together within the cosima-cookbook but this causes issues for downstream analysis.
 - Replace uses of the cosima-cookbook `compute_by_blocks` function with regular `compute`s. This function was a workaround, but is no longer necessary with dask's scheduling update in 2022.11.0.

The notebook was run using an NCI ARE JupyterLab `normalbw` `Large` (7 cpus, 32 GB) instance. The notebooks runs using the `dask-2022.11.0` environment but crashes with memory issues using the `dask-2022.10.2` environment.
