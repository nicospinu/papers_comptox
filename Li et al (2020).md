* https://dx.doi.org/10.1021/acs.chemrestox.9b00259

* **Background:**
  * How different types of models can complement and potentially help each other to afford the best prediction accuracy for a given chemical
  * The LD50, the amount of a chemical resulting in the death of 50% of a group of test animals, is a commonly used measurement to compare the acute toxic potential of different chemicals: the smaller the value, the more toxic is the chemical
  * The LD50 value predictions required a continuous regression modeling approach, while the end points of “very toxic” chemicals and “nontoxic” chemicals were binary classifications and the last two end points of EPA or GHS hazard categories were multiclass models
  * Developing new strategies to better synergize regression and classification models could ultimately boost the performance, interpretability, and applicability domain of *in silico* models for chemical toxicity prediction

* **Aim:**
  * Novel, dual-layer hierarchical modeling method to fully integrate regression and classification QSAR models for assessing rat acute oral systemic toxicity, with respect to regulatory classifications of concern

* **Data:**
  * Rat acute oral toxicity data
  * The training and external test sets were curated according to standard curation protocols developed earlier: 
    * (1) remove counterions in the salts and neutralize; 
    * (2) remove mixtures; 
    * (3) filter molecules comprising the following elements only: H, C, N, O, F, Br, I, Cl, P, and S; 
    * (4) normalize the structures of specific chemotypes, such as aromatic and nitro groups;
    * (5) identify, analyze, and remove structural duplicates and, if necessary, conflicting labels
  * All chemicals were curated using KNIME

* **Molecular descriptors:**
  * Molecular descriptors were computed on the basis of 2D molecular structures
  * Bit-based and Count-based Morgan fingerprints with radius of 3 (ECFP633), MACCS key fingerprints, and RDKit descriptors were computed using the RDKit package in Python
  * Mordred descriptors were computed using the Mordred package in Python
  * The zero/near zero variance descriptors and highly correlated pairs of descriptors of the training set were identified and filtered out. If the absolute correlation between any pair of descriptors was larger than 0.9, the descriptor with the largest mean was removed

* **Approach:**
  * For regression models, the target end point is the experimental logLD50 (mmol/kg) values of the molecules
  * For binary models, the training end point is a defined label (toxic/ nontoxic), and for the multiclass models, the training targets are the toxicity categories (categories I, II, III, IV) defined by the U.S. EPA criterion for acute oral systemic toxicity
  * The first layer models trained with computed chemical descriptors/fingerprints are called the base models, and the second layer models trained by the stacking base models’ out-of-fold predictions are called the hierarchical models
  * In order to build powerful stacking (2nd layer) models, it is crucial to build a diverse set of first-layer models
  * In order to enhance the model diversity, base models were trained by using various combinations of machine learning algorithms and chemical descriptors/fingerprints
  * They chose the combinations of four machine learning algorithms (RF, SVM, kNN, and XGBoost) and five chemical descriptors/fingerprints (ECFP6_Bits, ECFP6_Counts, MACCS keys, RDKit descriptors, and Mordred descriptors) to build base regression, binary, and multiclass models
  * For each end point, a diverse set of 20 models was built (60 base models total)
  * The hyperparameters of all base models were optimized through grid search using 5-fold cross-validation
  * To investigate the chemical space of the full data set (11 056 molecules), a t-Distributed Stochastic Neighbor Embedding40 (t-SNE) was calculated using the Bit-based ECFP6 (2048 bits)

* **Model performance:**
  * All models were evaluated with 10-fold cross validation and the external test set
  * Regression models: root-mean-square-error (RMSE) and the coefficient of determination
  * Classification models: Accuracy, sensitivity, specificity, balanced accuracy, recall, precision, F1-score, and Matthews correlation coefficient
  * The area under receiver operating characteristic curve (AUROC) is also reported for binary models

* **Key learnings:**
  * Different types of base models can learn the training data from different perspectives (via different machine learning techniques and molecular descriptors) and then complement each other in a stacking-like workflow, resulting in a boost of prediction performance and applicability domain for those hierarchical (H-)QSAR models
  * This significant boost of performances shows that the hierarchical models actually benefitted from the stacking procedure
