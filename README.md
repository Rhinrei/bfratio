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
- Computes B/F ratio and richness/diversity ratios.

## Inputs (file paths used)

The Rmd references these local files (update paths if your data location differs):

- `data/healthy_16s.xlsx`
- `data/healthy_its.xlsx`
- `data/16S featureTable.sample.g.absolute.xlsm`
- `data/featureTable.sample.g.absolute.xls`

