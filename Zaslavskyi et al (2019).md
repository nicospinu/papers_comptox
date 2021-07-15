* https://doi.org/10.1016/j.comtox.2019.01.001

* **Aim:** 
  * Proposing a systematic ensembling method for virtual toxicity screening, a prediction model for toxicity-related bioactivity pre-screening

* **Data:**
  * The TOX21 and TOXCAST datasets obtained from the DeepChem package
  * For the individual models they trained, they utilised physical chemicals descriptors, PubChem molecular fingerprints, and SMILES n-grams

* **Approach:**
  * XGB, DNNs, and GCNs
  * The multi-task gradient boosting model was trained on an entire dataset simultaneously by stacking all task-specific data together and  adding a descriptor representing the identity of the corresponding task
  * GCNs can be seen as a more general version of molecular circular fingerprint, where fingerprints are learned directly from the dataset

* **Model optimization:**
  * All model hyperparameters were optimized using the validation set

* **Model performance:**
  * Three types of cross-validation experiments were conducted based on random, scaffold and index splits
  * For random splitting, all chemicals were divided randomly into three groups: training (80%), validation (10%) and test sets (10%)
  * When using scaffold splitting, all chemicals were grouped according to their scaffolds, such that chemicals with the same scaffold were always assigned to the same set (training, validation, or test)
  * Index based splitting follows the natural order of rows in the dataset, it uses first 80% rows as the training set and the following 10% and 10% as validation and test sets

* **Feature importance:**
  * For NNs, they used a permutation feature importance technique. For each feature, they randomly shuffled the values associated to this feature and the k most correlated features, and computed the average AUC degradation over 5 folds, for k=0, 5 and 10. The lower the AUC, the more important the feature

* **Key learnings:**
  * Showed that models trained directly on SMILES features can be competitive with those trained on molecular fingerprint representations for both TOX21 and TOXCAST
  * Many of the most important fingerprint descriptors are related to the size of the molecule, indicating that size characteristics might be a critical indicator for bioactivity prediction
