# sm-bc4-profile
Simple and ready-to-go profile for Snakemake on BlueCrystal 4 with sensible defaults, based on [the default slurm profile](https://github.com/Snakemake-Profiles/slurm)

## Prerequisites
This profile requires Cookiecutter to run. You can install it with

```
$ python3 -m pip install --user cookiecutter
```
or, if under a conda environment:
```
conda config --add channels conda-forge
conda install cookiecutter
```
## Setup
In your project folder, run
```
git clone https://github.com/GiulioCentorame/sm-bc4-profile.git
```

To run Snakemake with the profile, add the `--profile bc4` flag, e.g.

```
snakemake -np -c1 --profile sm-bc4-profile
```

To add rule-dependent settings for the job submission (or override the default ones), add entries to `cluster_profile.yaml` with the following YAML syntax:

```
__default__:
  partition: veryshort
  mail-type: ALL,TIME_LIMIT_80
  output: logs/{rule}/{rule}-{wildcards}-%j.out
  mem: 20000M
  nodes: 1
  cpus-per-task: 12
name_of_the_rule:
  partition: cpu
  setting-name: value
  another-setting: dunno
```
The job for that rule will be run as `sbatch --partition=cpu --setting-name=value --another-setting=dunno`

The full list of possible flags is [here](https://slurm.schedmd.com/sbatch.html)
