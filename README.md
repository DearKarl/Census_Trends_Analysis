# Census Latent Patterns in England & Wales
### Bayesian latent modelling, dimensionality reduction, and clustering on ONS Census data

This repository implements an analytics for exploring 2011 & 2021 Census data from England and Wales. The workflow integrates multi-table census data (accommodation type, tenure, occupancy, and car availability), harmonises 2021 local authority geographies to the 2011 framework, constructs Bayesian latent indices with credible intervals, applies dimensionality reduction and clustering (PCA–t-SNE, UMAP, K-Means), and exports Tableau-ready CSVs for comparative visualisation.  

## Background  

Cross-year socio-demographic comparison in the UK is challenged by two issues: (1) administrative geography changes between 2011 and 2021, and (2) high-dimensionality of census tabulations. Raw tables obscure interpretable social structures, while geography mismatches prevent valid temporal comparisons.  

This project resolves these barriers by:  
- aligning 2021 geography codes to 2011 units via TF-IDF name similarity, token rules, and manual splits;  
- deriving latent constructs** such as deprivation, housing strain, tenure instability, and mobility access with **Bayesian Confirmatory Factor Analysis (CFA);  
- applying non-linear embeddings (UMAP, t-SNE) and clustering to reveal structural groupings;  
- producing uncertainty-aware, Tableau-ready outputs for visual analytics of temporal change.  

## Project Goal

The aim of this project is to develop a reproducible pipeline that harmonises the 2011 and 2021 Census geographies to enable consistent cross-year analysis, constructs latent socio-demographic indices through Bayesian inference, applies dimensionality reduction and clustering techniques to project indicators and indices into low-dimensional spaces for the identification of regional patterns, and produces exportable datasets that facilitate the clear visual comparison of socio-economic trends across the two census years.

## Methods Overview  

- **Data Harmonisation**:  
  - Load and audit Census 2011 (QS402EW, QS405EW, QS412EW, QS416EW) and 2021 (TS044, TS054) datasets.  
  - Align 2021 codes to 2011 geography using TF-IDF cosine similarity, token-level matching, and explicit split/merge rules.  
  - Standardise all variable names to **snake_case** for clean processing.  

- **Bayesian Latent Modelling**:  
  - Group observed indicators into predefined constructs (deprivation, housing strain, tenure instability, mobility access).  
  - Fit Bayesian CFA models with PyMC, using ADVI for variational inference.  
  - Export posterior means and 95% credible intervals for each index.  
  - Extend CFA to accommodation and tenure features for 2011 vs 2021 latent comparisons.  

- **Dimensionality Reduction & Clustering**:  
  - Apply PCA→t-SNE for observed 2011 indicators.  
  - Use UMAP for latent indices and 2011–2021 feature sets.  
  - Cluster embeddings with **K-Means (k=5)** independently per year.  
  - Profile clusters via within-cluster proportions, scaled to “relative scores” for interpretability.  

- **Outputs**:  
  - Long-format latent data, wide-format year pivots, embedding coordinates with cluster labels, and normalised cluster profiles.  
  - Files are written to `Dashboard*/` directories for Tableau dashboards.  

## Data Sources  

- [ONS Census 2011](https://www.ons.gov.uk/census/2011census) – QS402EW, QS405EW, QS412EW, QS416EW  
- [ONS Census 2021](https://www.ons.gov.uk/census/2021census) – TS044, TS054  

All data © Crown copyright and database right. Licensed for re-use under the Open Government Licence.  

## References  

- Jöreskog, K. G. (1969). *A general approach to confirmatory maximum likelihood factor analysis.*  
- Brown, T. A. (2015). *Confirmatory Factor Analysis for Applied Research* (2nd ed.).  
- Kucukelbir, A., Ranganath, R., Gelman, A., & Blei, D. (2017). *Automatic Differentiation Variational Inference.* JMLR.  
- Salvatier, J., Wiecki, T., & Fonnesbeck, C. (2016). *Probabilistic programming in Python using PyMC3.* PeerJ Computer Science.  
- Kumar, R. et al. (2019). *ArviZ: A unified library for exploratory analysis of Bayesian models.* JOSS.  
- Van der Maaten, L., & Hinton, G. (2008). *Visualizing data using t-SNE.* JMLR.  
- McInnes, L., Healy, J., & Melville, J. (2018). *UMAP: Uniform Manifold Approximation and Projection.*  
- MacQueen, J. (1967). *Some methods for classification and analysis of multivariate observations.* Proc. 5th Berkeley Symp.  
- Pedregosa, F. et al. (2011). *Scikit-learn: Machine Learning in Python.* JMLR.  

---

> Repository maintained by the project team. Contributions and feedback welcome.  
