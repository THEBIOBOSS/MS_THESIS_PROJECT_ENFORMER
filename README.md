# Enformer Performance Evaluation: Leveraging Deep Learning to Interpret Genetic Variation in Prostate Cancer

## Project Description

This repository contains the main implementation code used in my Master's thesis — [**Enformer Performance Evaluation: Leveraging Deep Learning to Interpret Genetic Variation in Prostate Cancer**](https://urn.fi/URN:NBN:fi:tuni-202507257801) — conducted at the Computational Biology lab under the supervision of **Professor Matti Nykter**.

The project employed a deep learning sequence-based model, Enformer, to predict the effects of both coding and non-coding variants on gene expression. The concept was to explore the potential of deep learning in interpreting genetic variation in prostate cancer, specifically focusing on variations found in non-coding regulatory regions of the genome such as promoters and enhancers that control gene expression. It is known that 98% of the genome is non-coding, and very little is understood about its functionality. Deep learning approaches have the potential to unlock insights into this vast, unexplored territory. Several sequence-based models like Basenji and Enformer have already been developed, and ongoing research continues to advance this field. The goal of the project was to assess the capability of the generalized Enformer model to predict the functional impact of genetic variants linked to prostate cancer, to determine whether the model could enhance our understanding and interpretation of human genetic variation and biology in this context.

---

## Code Source and Attribution

The base implementation is adapted from the official DeepMind Enformer repository:

> Avsec, Ž., Agarwal, V., Visentin, D. et al. *Effective gene expression prediction from sequence by integrating long-range interactions.* Nat Methods 18, 1196–1203 (2021). [https://doi.org/10.1038/s41592-021-01252-x](https://doi.org/10.1038/s41592-021-01252-x)

**Original code:** [google-deepmind/deepmind-research — enformer](https://github.com/google-deepmind/deepmind-research/tree/master/enformer)

Modifications and additions were made to adapt the original open-source implementation for this project's prostate cancer variant analysis pipeline.

---

## Modifications and Additions

The following changes were made to the original Enformer code for this project:

- **Data directory paths** updated to point to HPC cluster paths (`/lustre/scratch/...`) and project-specific data files.
- **Prostate cancer variant data** from the [West Coast Dream Team (WCDT)](https://quigleylab.s3.us-west-2.amazonaws.com/datasets/2018_04_15_WCDT_somatic_vcf.tar) somatic SNP VCF dataset was introduced in place of the original ClinVar dataset.
- **Prostate-specific target filtering** added to isolate relevant DNASE, ChIP, and CAGE tracks (e.g., prostate epithelial cells, prostate cancer cell lines PC-3 and DU145) from the Basenji2 target list.
- **Batch variant scoring pipeline** implemented to process all patient VCF files, sorted by variant count, scoring each variant against all prostate-relevant Enformer output tracks and saving results to VCF and Excel formats.
- **Automated visualization pipelines** added for both coding (missense) and non-coding variants — iterating over gene-level VCF files and saving per-variant track plots to organized output directories.
- **Logging** added to record processing statistics and timestamps for reproducibility.

---

## Notebook Overview

**`enformer-usage-mythesiswork.ipynb`**

This notebook demonstrates the workflow used to:

- Load the Enformer model from TensorFlow Hub and the reference human genome (hg38)
- Filter and extract prostate-relevant genomic targets from the Basenji2 human targets list
- Make gene expression predictions for example genomic intervals and visualize selected prostate tracks
- Compute contribution (gradient × input) scores to identify regulatory sequence importance
- Score individual variants and visualize reference vs. alternate allele predictions across prostate-specific CAGE, DNASE, and ChIP tracks
- Batch-process somatic SNP VCF files from prostate cancer patients, scoring all variants against prostate-relevant Enformer output features using both PCA-normalized (top 20 PCs) and z-score-normalized (all 5,313 features) scoring models
- Save scored variant results to VCF and Excel output files with processing logs

---

## Code Availability

The main implementation code for the Enformer workflow is provided in this repository. Supporting scripts and auxiliary components used in the complete project pipeline (e.g., variant annotation with SnpEff, upstream data preprocessing) are not included here, as they were part of the broader research environment. Guidance on the full pipeline can be provided upon request.

---

## Files in This Repository

| File | Description |
|------|-------------|
| `README.md` | This file |
| `enformer-usage-mythesiswork.ipynb` | Main Enformer implementation notebook |

---

## License

The original Enformer code is licensed under the **Apache License 2.0** by DeepMind Technologies Limited. See [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0) for details.