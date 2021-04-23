# IBIEM 2021 Plastics project

## Information about the dataset

The project goal is to identify 

Samples were collected from four sites:
1. LF : Soil from a landfill in Durham, NC
2. ER : Contaminated sediment from the Elizabeth River, VA
3. AS : Activated sludge from a wastewater treatment plant, Durham, NC
4. RC : Soil from a recycling center, Durham County, NC

Each sample was mixed and aliquoted into capped bottles under one of four conditions
1. Ctrl : Control, containing only a minimal medium without carbon to resuspend the matrix
2. S : Styrene, sample exposed to volatilized styrene plus the minimal medium
3. PS : Polystyrene, sample contained powdered polystrene in addition to the minimal medium
4. PSS : Styrene and polystyrene, as above, in addition to the minimal medium

There is a single replicate per timepoint from weeks 1 (inoculation) to 7, and a final timepoint at week 12.

## Computing environment

To replicate this analysis, a Docker container can be downloaded from Docker Hub using the command docker pull ibiem/docker_rstudio_ibiem2020:2020_v004 (using Docker) or singularity pull docker://ibiem/docker_rstudio_ibiem2020:2020_v004 (using Singularity).

## Data availability

Data occur as part a larger sequencing run performed at Argonne National Labs, and are available in the /data directory in the Docker environment.

## Code repository

To replicate analyses, clone the git repository (this repository) using: git clone git@github.com:bpetrone/plastics.git.

## Processing steps

Finally, run (in the Docker image described above) the Rmarkdown documents listed below. The Rmarkdown documents must be run as follows:

Begin with:
1. raw_to_phyloseq.Rmd: Identifies sequence variants in raw data with DADA2, and converts to a phyloseq object.
2. (Data imputed from raw phyloseq object with separate Python script): Imputes ASV abundances for missing timepoints 8-11.
3. imputed_data.Rmd: Returns imputed data tabe to phyloseq object format.

As interested, at this point any of the following scripts can be run:
- alpha_diversity.Rmd
- beta_diversity.Rmd
- lefse.Rmd
- streamgraph.Rmd
