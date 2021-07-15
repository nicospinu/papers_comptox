* https://doi.org/10.1186/s13321-019-0384-1 

* **Background:**
  * The logarithmic acid dissociation constant pKa reflects the ionization of a chemical, which affects lipophilicity, solubility, protein binding, and ability to pass through the plasma membrane
  * pKa affects chemical absorption, distribution, metabolism, excretion, and toxicity properties
  * Multiple proprietary software packages exist for the prediction of pKa, but no free and open-source programs exist for this purpose

* **Aim:**
  * Development of *in silico* models for the prediction of the most acidic and most basic pKa values for a chemical, rather than the values for all potential ionizable sites, and make both the data and models available as free and open-source tools

* **Data collection:**
  * The experimental strongest acidic and strongest basic pKa values in water for 7912 chemicals were obtained from DataWarrior, a freely available software package
  * Continuous molecular descriptors, binary fingerprints, and fragment counts were generated using PaDEL
  * The collected chemical structures were analyzed for diversity using Toxprint chemotypes showing that the chemical space is heterogenous
  * The accuracy of the data was checked: chemicals having at least five pKa measurements were identified and 75 of these were randomly selected and compared to literature values. Literature pKa data were found for 80% of the chemicals and 93% of these chemicals were within ± 0.30 pKa units of the DataWarrior values. Considered this to indicate that the DataWarrior pKa values were sufficiently robust to support further investigation

* **Data curation:** 
  * KNIME workflow used to exclude inorganic chemicals and mixtures; removes salts, solvents, and counterions; identifies duplicates; and normalizes tautomers (e.g., nitro mesomers and keto-enol forms, zwitterions are not modified)
  * PaDEL Descriptors: remove highly correlated features and near-zero variance features, and continuous descriptors were scaled

* **Feature selection:**
  * Three feature-reduction techniques were applied to the binary fingerprints and fragment counts descriptors: remove (1) data in which features (columns) of all zeros and all ones were deleted, (2) as previous but with highly correlated features removed, and (3) as previous but with low-variance features removed

* **Approach:**
  * (1) support vector machines (SVM) combined with k-nearest neighbors (kNN), (2) extreme gradient boosting (XGB) and (3) deep neural networks (DNN)
  * Different options of modeling the data for each approach were applied: (1) all chemicals with replicates removed, (2) low variability replicates included, (3) all data included
  * Since acidic and basic data sets were modelled separately, in order to predict pKa for a new chemical, it was necessary to decide whether the chemical had an acidic, basic, or amphoteric structure. A three-class categorical model was developed for this purpose. Genetic algorithms (GA) were used to find the optimal subset of molecular descriptors that differentiated the three
  * The DNN learning models were built using the opensource deep learning libraries Keras and Tensorflow

* **Model performance:**
  * Root-mean squared error (RMSE) and coefficient of determination (R<sup>2</sup>)
  * Two commercial pKa predictors from ACD/Labs and ChemAxon were used to benchmark the three best models developed herein

* **Applicability domain:**
  * Since binary fingerprints were employed to build the predictive models, the Jaccard-Tanimoto dissimilarity index was used as the distance metric to assess the applicability domain and accuracy estimates

* **Model benchmark:**
  * To further validate the three models and assess their predictivity, a large external data set from existing software that was not used during the modeling process was used for this purpose

* **Key learnings:**
  * SVM model was better than the DNN model for chemicals with a basic pKa
  * The DNN model for chemicals with an acidic pKa was better than the SVM and XGB models
  * By excluding the extreme values that are the source of divergence between the commercial tools and are absent in DataWarrior, the overall concordance between the benchmark datasets and the three models increased
