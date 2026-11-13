# SECSWATH_ComplexCentricAnalysis

Complex-centric analysis of SEC-SWATH-MS data with
[CCprofiler](https://github.com/CCprofiler/CCprofiler): the R workflow and example data that
accompany the Nature Protocols paper below. It starts from the peptide-level output of
[SECSWATH_PeptideCentricAnalysis](https://github.com/CCprofiler/SECSWATH_PeptideCentricAnalysis)
and ends with a table of detected protein complexes at controlled FDR.

**Developed by M. Heusel and I. Bludau**, for the publication:

> Bludau, I., Heusel, M., Frank, M., Rosenberger, G., Hafen, R., Banaei-Esfahani, A., van Drogen, A., Collins, B.C., Gstaiger, M., Aebersold, R., 2020. Complex-centric proteome profiling by SEC-SWATH-MS for the parallel detection of hundreds of protein complexes. *Nature Protocols* 15, 2341–2386. https://doi.org/10.1038/s41596-020-0332-6

Also cite: Heusel, M., Bludau, I., Rosenberger, G., Hafen, R., Frank, M., Banaei‐Esfahani, A., van Drogen, A., Collins, B.C., Gstaiger, M., Aebersold, R., 2019. Complex‐centric proteome profiling by SEC‐SWATH‐MS. *Mol Syst Biol* 15, MSB188438. https://doi.org/10.15252/msb.20188438

## Workflow

1. Import peptide-level quantities (OpenSWATH, or any tool in long/wide format) with the fraction annotation
2. Molecular-weight calibration of SEC fractions; UniProt annotation
3. Missing-value imputation, consecutive-ID and sibling-peptide-correlation (FDR) filtering
4. Grid search for optimal feature-finding parameters
5. Protein-centric analysis: peptide co-elution peak groups per protein, scored at FDR
6. Protein quantification (top-N peptides)
7. Complex-centric analysis: CORUM or BioPlex-derived target queries plus decoys, complex feature finding, MW filtering, scoring, collapsing to unique complex signals

## Files

| File | Content |
|---|---|
| `CCprofiler_analysis.R` | Complete analysis script |
| `CCprofiler_analysis_protocol.R` / `.pdf` | Annotated version rendered as the protocol supplement |
| `quantData_OpenSWATH.rds` | Peptide-level quantities from the peptide-centric pipeline |
| `example*.tsv` | Example peptide data (long/wide), fraction annotation, calibration and trace annotation |
| `corumComplexHypothesesRedundant.csv`, `BioPlexPPIs.tsv` | Prior complex/interaction knowledge |

## Usage

```r
install.packages(c("devtools", "data.table"))
devtools::install_github("CCprofiler/CCprofiler")
# from a clone of this repository:
source("CCprofiler_analysis.R")
```

---
<sub>README optimized with Claude Opus 5.5.</sub>
