Enformer Performance Evaluation: Leveraging Deep Learning to Interpret Genetic Variation in Prostate Cancer

This repository contains code developed as part of my master’s thesis, Enformer Performance Evaluation: Leveraging Deep Learning to Interpret Genetic Variation in Prostate Cancer
, conducted in a Computational Biology lab under the supervision of Professor Matti Nykter.

The project explores the potential of deep learning to interpret the effects of genetic variation, particularly in non-coding regulatory regions of the genome (such as promoters and enhancers) that control gene expression. The focus is on prostate cancer-associated variants, leveraging the sequence-based deep learning model Enformer.

Project Overview

The goal of this thesis was to assess whether the generalized Enformer model can predict the functional impact of genetic variants linked to prostate cancer. Variants in non-coding regions make up 98% of the genome, yet their function remains largely unexplored. By applying Enformer to both coding and non-coding variants, the project aims to improve our understanding of human genetic variation in the context of prostate cancer.

Key aspects of the project include:

Using Enformer to predict gene expression changes caused by specific variants.

Visualizing contribution scores for variant-centered sequences.

Applying the model to prostate cancer-specific genomic data.

Evaluating the model’s potential for variant interpretation in both coding and non-coding regions.

Code Origin

The implementation of Enformer used in this project is based on the original code from DeepMind:

GitHub repository: Enformer by DeepMind

Original paper: Avsec, Ž., Agarwal, V., Visentin, D., et al. Effective gene expression prediction from sequence by integrating long-range interactions. Nat Methods 18, 1196–1203 (2021). https://doi.org/10.1038/s41592-021-01252-x

Note: All modifications, including preprocessing, variant handling, and visualizations, were implemented by me to adapt the model for prostate cancer variant data.

Repository Contents

README.md – this file.

enformer-usage-mythesiswork.ipynb – main Jupyter notebook demonstrating usage of the Enformer model, including:

Loading the reference genome and variant data.

Extracting variant-centered sequences.

Making predictions using Enformer.

Computing contribution scores and visualizing variant effects.

Processing both coding (missense) and non-coding variants.

⚠️ The full dataset and additional support files for complete implementation are not included in this repository. Only the main code for demonstration is provided.

Usage

Ensure you have access to GPU for faster predictions.

Install required dependencies:

pip install tensorflow tensorflow-hub kipoiseq pyfaidx pandas matplotlib seaborn joblib

Update paths in the notebook to point to your genome FASTA file, VCF files, and transformation files.

Run cells sequentially to:

Load the Enformer model.

Extract sequences and make predictions for both reference and alternate alleles.

Compute contribution scores.

Generate visualizations for prostate cancer-specific variants.

License

The original Enformer code is licensed under the Apache License 2.0
. Modifications in this repository are for academic and research purposes.