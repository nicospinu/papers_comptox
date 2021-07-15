* https://dx.doi.org/10.1021/acs.chemrestox.9b00305 

* **Aim:**
  * To build optimal prediction models for various human *in vivo*/organ-level toxicity end points (extracted from ChemIDPlus) using chemical structure and Tox21 *in vitro* quantitative high-throughput screening (qHTS) bioactivity assay data model 14 human toxicity end points pertaining to vascular, kidney, ureter and bladder, and liver organ systems

* **Data:**
  * *In vitro* data from Tox21
  * For modeling purposes, curve rank was used as a measure of chemical activity. Curve rank is a number between 9 and −9, where a positive value denotes activation and a negative value denotes inhibition. Compounds with a good quality concentration−response curve corresponding to high potency and efficacy are assigned large absolute curve rank values (>0.5) and labeled as active (1), whereas compounds with absolute curve rank values 0.5 and below are labeled as inactive (0)
  * *In vivo* human data from https://chem.nlm.nih.gov/chemidplus/ 
  * Fingerprints ToxPrint and ECFP4 from KNIME CDK package
  * Structures were further salt stripped using the JChem package from ChemAxon. In cases of heavy metal salts and inorganics, the metal ion was retained after desalting. SMILES were converted to InChI keys in order to identify structure replicates

* **Feature selection:**
  * Fisher’s exact test with p value, importance scores from XGboost, and the RF algorithm
  * For Fisher’s exact test, the features selected by 30 independent p values ranging from 0.01 to 0.3 were used to train the models and the feature sets that achieved the best performance were selected to build the final model
  * The “xgboost” and “Random Forest” packages were applied to retrieve feature importance scores, respectively. These scores were then ranked to obtain the top 50 features

* **Approach:**
  * Three typed of models: assay activity (activity-only models), chemical structure (structure-only models), and models based on combinations of structure and activity data

* **Model performance:**
  * 5-fold cross validation was applied with the data set randomly divided into five parts, four parts for training and one part for testing 
  * To ensure the robustness of our results, the random partitioning process was repeated 20 times for each model
  * Area under the receiver operating characteristic curve (AUC-ROC), balanced accuracy (BA), and Matthews correlation coefficient (MCC)

* **Key learnings:**
  * Model performance was found to be dependent on the specific data set, model type, and feature selection method used
  * In addition, chemical structure and assay data showed different levels of contribution to the prediction of different toxicity end points 
  * Although *in vitro* assay data, when combined with chemical structure, slightly improved the predictive accuracy for most end points (11 out of 14), a noteworthy finding was the near equal success of the structure-only models, which do not require Tox21 qHTS screening data, and the relatively poor performance of assay-only models
  * Bioactivity and structure – case dependent performance
  * XGboost turned out to be the best feature selection method
  * The end points with slightly less predictive models (i.e., cardiac (0.74   0.01) and gastrointestinal (0.72   0.01)), may have more complex toxicity mechanisms and need data on additional targets that are not covered by the current Tox21 assays to improve model performance
