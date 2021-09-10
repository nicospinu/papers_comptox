# Publications on Computational Toxicology

### About this repository
I created this repository for the purpose of understanding what the current trends are in the development of computational models in toxicology, especially in the context of QSARs/QSPRs. It includes a series of personal notes that summarise main ideas of recent published articles in peer-reviewed Journals that can serve as promising examples.

### QSARs/QSPRs definition
Quantitative structure-activity relationships (QSARs) and quantitative structure-property relationships (QSPRs) models are mathematical models developed to assess chemical induced toxicity using continuous (regression, e.g., LD50) or discrete (classification, i.e., binary, multi-classes) predictions based on molecular descriptors that are computationally calculated using a range of software, or determined experimentally from the molecules themselves to describe the structure of the chemical, e.g., the relationship between physico-chemical or biochemical properties (e.g., LogP) and biological activity. It allows building the model based on the correlation between the variable of interest (target toxicity) and chemical structure and associated properties. 
<img src="QSAR%20Flow-chart.png" alt="QSAR%20Flow-chart" width="700"/>

### General workflow
<img src="QSAR%20workflow.png" alt="QSAR%20workflow" width="700"/>


### Overview of the publications studied herein

Reference | LR | KNN | SVM | RF | NB | XGB | ANN | DNN | GCN | Endpoint(s)
--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | ---
[Mansouri et al (2019)](https://github.com/nicospinu/papers-comptox/blob/main/Mansouri%20et%20al%20(2019).md) |  |  | Y |  |  | Y |  | Y |  | pKa
[Zaslavskyi et al (2019)](https://github.com/nicospinu/papers-comptox/blob/main/Zaslavskyi%20et%20al%20(2019).md) |  |  |  |  |  | Y |  | Y | Y | Bioactivity
[Li et al (2020)](https://github.com/nicospinu/papers-comptox/blob/main/Li%20et%20al%20(2020).md) |  | Y | Y | Y |  | Y |  |  |  | Acute toxicity
[Xu et al (2020)](https://github.com/nicospinu/papers-comptox/blob/main/Xu%20et%20al%20(2020).md) |  |  | Y | Y | Y | Y | Y |  |  | 14 organs
[Garcia de Lomana et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Garcia%20de%20Lomana%20et%20al%20(2021).md) | Y |  | Y | Y |  | Y |  | Y | | MIEs thyroid
[Jain et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Jain%20et%20al%20(2021).md) |  |  |  | Y |  |  |  | Y | Y | Acute toxicity
[Li et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Li%20et%20al%20(2021).md) | Y | Y | Y | Y |  | Y |  | Y |  | DILI
[Liu et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Liu%20et%20al%20(2021).md) |  |  | Y | Y |  | Y |  |  |  | BBB
[Rathman et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Rathman%20et%20al%20(2021).md) | Y | Y | Y | Y |  |  | Y |  |  | DILI
[Ulrich et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Ulrich%20et%20al%20(2021).md) |  |  |  |  |  |  |  | Y |  | LogP
[Zhoue et al (2021)](https://github.com/nicospinu/papers-comptox/blob/main/Zhoue%20et%20al%20(2021).md) | Y |  | Y | Y |  | Y |  |  |  | DIR

*LR: Linear Regression; KNN: k-Nearest Neighbors; SVM: Support Vector Machine; RF: Random Forest; NB: Naïve Bayes; XGB: eXtreme Gradient Boosting; ANN: Artificial Neural Network; DNN: Deep Neural Network; CGN: Graph Convolutional Network. Y: Yes. pKa = − log10 Ka (acid dissociation constant also called the protonation
or ionization constant). MIEs: Molecular initiating Events. DILI: Drug-Induced Liver Injury. BBB: Blood-Brain Barrier. LogP: logKow (the octanol–water partition coefficient Kow). DIR: Drug-induced rhabdomyolysis*

### Current trends
* Multi-task modelling
* Battery of *in silico models* and combination of MLs
* Ensembling learning (e.g., models trained on different fingerprints/descriptors)
* Combination of continuous regression with classification modeling approaches
* Consensus model (the predicted toxicity is estimated by taking an average of the predicted toxicities from each single model)
* Model interpretation and explainability including model benchmark (comparison with other models, datasets)
* The choice of molecular descriptors’ on the impact on model performance
* Sequential feature selection strategy
* Uncertainty quantification (e.g., using Dempster-Shafer decision theory)


### Recommended references
Books:
* [In Silico Toxicology: Principles and Applications](https://doi.org/10.1039/9781849732093)
* [Recent Advances in QSAR Studies: Methods and Applications](https://doi.org/10.1007/978-1-4020-9783-6)
* [In Silico Methods for Predicting Drug Toxicity](https://doi.org/10.1007/978-1-4939-3609-0)
* [The History of Alternative Test Methods in Toxicology](https://doi.org/10.1016/C2016-0-00193-6)

Other links:
* [OECD (Q)SAR landing page](https://www.oecd.org/env/ehs/risk-assessment/introductiontoquantitativestructureactivityrelationships.htm)
* [OECD Guidance Document on the Validation of (Q)SAR Models](https://www.oecd.org/officialdocuments/publicdisplaydocumentpdf/?doclanguage=en&cote=env/jm/mono(2007)2)
* [JRC QSAR Model Database](https://ec.europa.eu/jrc/en/scientific-tool/jrc-qsar-model-database)
* [VEGA Hub of IRFMN](https://www.vegahub.eu/)
* [Wang et al (2020)](https://dx.doi.org/10.1021/acs.chemrestox.0c00316)
