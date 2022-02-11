# sm-bc4-profile
Simple and ready-to-go profile for Snakemake on BlueCrystal 4 with sensible defaults, based on [the default slurm profile](https://github.com/Snakemake-Profiles/slurm)

## Setup

```
mkdir -p bc4 && cd bc4 &&
git clone https://github.com/GiulioCentorame/sm-bc4-profile.git
```

To run Snakemake with the profile, add the `--profile bc4` flag to the Snakemake call, e.g.

```
Snakemake -np -c1 --profile bc4
```

To add rule-dependent settings for the job submission, add entries to `cluster_profile.yaml` with the following YAML syntax:

```
name_of_the_rule:
  setting-name: value
  another-setting: dunno
```
The job for that rule will be run as `sbatch --setting-name=value --another-setting=dunno`

The full list of possible flags is [here](https://slurm.schedmd.com/sbatch.html)
