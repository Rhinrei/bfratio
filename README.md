# bfratio Pipeline README

This repository centers on `pipeline.Rmd`, which runs the full analysis workflow for the bacteriome/mycobiome project.

## What `pipeline.Rmd` does

- Loads healthy and disease datasets for 16S and ITS.
- Filters low-abundance taxa.
- Builds taxonomy tables and phyloseq objects.
- Performs decontamination (with batch-aware handling).
- Rarefies and prepares patient-only datasets.
- Computes prevalence and group summaries by taxonomic rank.
- Calculates alpha diversity metrics and visualizations.
- Computes beta diversity (Bray-Curtis) and dispersion testing.
- Runs differential abundance (Wilcoxon on rarefied data).
- Runs DESeq2 on raw counts for candidate taxa.
- Performs focused validation for high log2FC fungi.
- Computes B/F ratio and richness/diversity ratios.

## Inputs (file paths used)

The Rmd references these local files (update paths if your data location differs):

- `data/healthy_16s.xlsx`
- `data/healthy_its.xlsx`
- `data/16S featureTable.sample.g.absolute.xlsm`
- `data/featureTable.sample.g.absolute.xls`

## Outputs

The pipeline prints summaries to the console and saves plots such as:

- `Differentially abundant bacterial genera in patients.png`
- `Differentially abundant fungal genera in patients.png`

Other plots are created in code and can be saved by uncommenting relevant blocks.

## How to run

Recommended (RStudio):
1. Open `pipeline.Rmd`.
2. Set the working directory to `C:\Users\Admin\Documents\bfratio` or the project root.
3. Knit the document (or run chunks sequentially).

Command line (if Rscript is on PATH):
```bash
Rscript -e "rmarkdown::render('pipeline.Rmd')"
```

## Notes

- Rarefaction uses fixed depths; several samples may be dropped if below the threshold.
- DESeq2 uses `poscounts` size factors and may be sensitive to zero inflation in small cohorts.
- Some sections are exploratory and intended for hypothesis generation; interpret with caution.

## Related files

- `diagnostic_check.R`: post-hoc diagnostics and sanity checks.
- `CONTRADICTION_EXPLAINED.md`: notes on Wilcoxon vs DESeq2 discrepancies.
- `PREVALENCE_ANALYSIS.md`: prevalence-focused notes.
