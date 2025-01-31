# Snakemake Tutorial for Make Users

This repository was forked from the [repository](https://github.com/riffomonas/make_tutorial) that accompanies Pat's [tutorial on GNU Make](http://www.riffomonas.org/reproducible_research/make/#1). The original tutorial focuses on replicating an analysis performed by FiveThirtyEight to [predict someone's age using their name](http://fivethirtyeight.com/features/how-to-tell-someones-age-when-all-you-know-is-her-name/). This project provides a parallel implementation in [Snakemake](https://snakemake.readthedocs.io/en/stable/index.html), a Python-based workflow management system.

The [`Snakefile`](https://github.com/SchlossLab/snakemake_tutorial/blob/master/Snakefile) in the master branch uses lots of Snakemake features that don't have parallels in Make. See the [`simple`](https://github.com/SchlossLab/snakemake_tutorial/tree/simple) branch for a version that more closely resembles the original [`Makefile`](Makefile).

## Datasets

The analysis draws names from two sources within the Social Security Administration:
* [Life tables](http://www.ssa.gov/oact/NOTES/as120/LifeTables_Tbl_7.html)
* [Name frequency](https://www.ssa.gov/oact/babynames/limits.html)

## Dependencies

All dependencies are listed in [`config/env.yaml`](config/env.yaml). You can install them manually using your preferred package manager(s), or use [`conda`](https://docs.conda.io/projects/conda/en/latest/index.html).

### Conda

If you don't already have `conda` installed, you can [download either Anaconda or Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/download.html) -- your preference. Anaconda3 includes everything, while Miniconda3 is faster to install. Be sure to pick the Python 3 version of the installer for your OS.

Download & install for 64-bit macOS:
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
bash Miniconda3-latest-MacOSX-x86_64.sh
```

Create an environment called `predict-age` with the dependencies we need:
```
conda env create -f config/env.yaml
```
Or give the environment whatever name you want using the flag `--name` or `-n`. (If you give it a different name, be sure to modify the environment name in [`pbs-torque/pbs-jobscript.sh`](pbs-torque/pbs-jobscript.sh).)

Activate the environment before running any code:
```
conda activate predict-age
```

See the [`conda` documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/index.html) for more information.
