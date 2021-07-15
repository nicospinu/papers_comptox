* https://doi.org/10.1021/acs.chemrestox.0c00343 

* **Aim:**
  * Developed ensemble models for predicting the BBB permeability of compounds using models trained based on different molecular fingerprints as base classifiers; compared with previous developed models; exemplified the substructures of two chemicals

* **Data:** 
  * Data from three studies (one dataset for external validation)
  * Molecular fingerprints from the PaDEL-Descriptor software

* **Data curation:**
  * Remove redundant data

* **Feature selection:**
  * This paper used two feature selection methods to filter the data set: 
    * (1) the nearZeroVar function in the R package caret was used to filter redundant or very similar features in all of the samples 
    * (2) the f indcorrelation function caret was used to filter out highly correlated features
  * Used the Tanimoto coefficient to assess whether a compound has one or more highly correlated feature (high-correlation feature filtering with a Tanimoto correlation coefficient threshold of 0.95)

* **Data imbalance:**
  * The resampling method Synthetic Minority Oversampling Technique (SMOTE) to effectively solve the problem of imbalanced data sets 
  * SMOTE generates extra examples from the minority class in an attempt to have its data set size match that of the majority class to combat the existing imbalance

* **Approach:**
  * Built qualitative models (Qualitative models can binary classify the BBB permeability of chemicals with high accuracy)
  * Three machine-learning methods, an SVM, an RF, and an extreme gradient boosting (XGBoost), were used to construct 27 base classifier models
  * The base classifiers were added to the ensemble machine-learning model based on the AUC value of each classifier from highest to lowest
  * RF: To better understand the contribution of several substructures related to blood−brain barrier permeability prediction, the mean decrease in the Gini coefficient (Mean Decrease Gini) was used to assess the importance of these substructures with the RF algorithm; the higher the mean decrease in the Gini coefficient, the closer the feature is to blood−brain barrier permeability prediction

* **Model performance:**
  * Internal validation involved 5-fold cross-validation with 100 repeats, and external validation was performed using an external validation data set
  * 5-fold cross-validation randomly divided the training set into 5 parts: 4 were used as a training set to build the model, and the remaining part was used to test the performance of the model. This process was repeated 5 times so that each part could be used as a test set. Following 5-fold cross-validation, a series of models with different performance results were obtained. All 5-fold cross-validations were based on 100 repeated experiments, and the average value of the 100 runs was used to evaluate the predictive performance of the model
  * Four performance indicators to evaluate the performance of the model: the ACC, AUC (area under the receiver-operating characteristic (ROC) curve), SPE (specificity), and SEN (sensitivity)

* **Key learnings:**
  * The ensemble model was superior to various base classifiers in terms of accuracy and AUC.
