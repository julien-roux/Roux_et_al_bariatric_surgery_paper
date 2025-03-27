# Rapid and long-lasting remodelling of the blood transcriptome following bariatric surgery


This Github repository provides the code, necessary data and settings for a conda environment allowing to reproduce the analyses presented in the Roux et al., 2025 paper

After cloning the repository from Github, you can create and activate the conda environment using:

```
cd Roux_et_al_bariatric_surgery_paper
conda env create -f environment.yml
conda activate Roux_et_al_bariatric_surgery_paper 
```

You can then start `R` from this environment with option `--vanilla`. Within R, a packages still need to be installed from Github (skip the suggested updates to other packages)

```
devtools::install_github("dviraran/xCell@7339410585bcccb2c2ceec2af47c8bcb646b42b2")

BiocManager::install("NMF") ## Version needed for CellChat is not on conda-forge
devtools::install_github("jinworks/CellChat@f6aa85d5ec6857d6cc0aaf05962b254d70d215c0")

## Reinstall preprocessCore to avoid this issue: https://github.com/bioconda/bioconda-recipes/issues/31420
BiocManager::install("preprocessCore", 
                     force = TRUE,
                     configure.args=c(preprocessCore = "--disable-threading"))
```

Finally you can run the code in R and generate an HTML document using:

```
rmarkdown::render("Roux_et_al_bariatric_surgery_paper.Rmd")
```
