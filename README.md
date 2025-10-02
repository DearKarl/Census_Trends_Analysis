# Census Latent Patterns Analysis in England & Wales

## Project Overview  

This project develops a reproducible analytics pipeline to explore socio-demographic structures in England and Wales using 2011 and 2021 Census data. It integrates multi-table census inputs (accommodation type, tenure, occupancy, car availability), harmonises geographies across years, constructs Bayesian latent indices with credible intervals, and applies machine learning techniques (PCA, t-SNE, UMAP, K-Means) to identify interpretable population patterns. Outputs are exported in Tableau-ready CSVs for comparative socio-economic visualisation.

## Background  

Socio-demographic comparison across Census years in England and Wales presents two major challenges:  
(1) **geographical inconsistency** caused by boundary changes between 2011 and 2021, and  
(2) **high-dimensionality** of census tabulations that obscures interpretable social patterns.  

This study aims to resolve these challenges through machine learning techniques. By harmonising geographies with text-matching algorithms, applying Bayesian latent variable models to derive socio-demographic constructs such as deprivation, housing strain, tenure instability, and mobility access, and embedding these indices into low-dimensional spaces using non-linear dimensionality reduction methods (t-SNE, UMAP), the pipeline enables interpretable discovery of underlying patterns. Clustering with K-Means then identifies structural groupings across local authorities, while uncertainty quantification through Bayesian inference ensures that cross-year comparisons remain statistically robust. The outcome is a reproducible machine learning workflow that transforms raw census tables into uncertainty-aware, interpretable, and visualisable socio-economic insights.   

## Key Features  

- **Geographical Harmonisation**: Resolve boundary inconsistencies between the 2011 and 2021 Census through automated text-matching algorithms, including TF-IDF similarity, token-based alignment, and explicit split–merge rules.  
- **Bayesian Latent Modelling**: Employ Bayesian Confirmatory Factor Analysis (CFA) with variational inference to construct latent socio-demographic indices. The Bayesian model integrates multiple observed indicators into theoretically informed constructs such as deprivation, housing strain, tenure instability, and mobility access.  
- **Uncertainty Quantification**: Use Bayesian inference to estimate posterior distributions, reporting posterior means with 95% credible intervals for each latent index.
- **Dimensionality Reduction and Clustering**: Apply representation learning methods (PCA, t-SNE, UMAP) to reduce the high-dimensional census space into low-dimensional manifolds. Unsupervised clustering with K-Means is used to detect emergent regional typologies and socio-economic groupings.  
- **Visual Analytics and Interpretability**: Export of harmonised, modelled, and clustered outputs in Tableau-compatible formats, supporting visualisation of spatial patterns and temporal dynamics in socio-economic change.  

## Dependencies  

- **Bayesian Modelling**: PyMC, ArviZ  
- **Machine Learning**: scikit-learn, umap-learn  
- **Data Processing**: pandas, numpy, scipy  
- **Visualisation**: matplotlib, seaborn, Tableau  


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

> Repository maintained by [DearKarl](https://github.com/DearKarl). Contributions and feedback welcome. 
