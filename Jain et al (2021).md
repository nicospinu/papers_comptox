* https://dx.doi.org/10.1021/acs.jcim.0c01164

* **Aim:** 
  * Multiple single and multitask models utilising random forest, deep neural networks, convolutional, and graph convolutional neural network approaches
  * They considered consensus approaches that combined predictions from different multitask learning approaches to predict acute toxicity

* **Data:** 
  * ChemIDplus (considered the data from three measurement units: mg/kg, μg/kg, and ng/kg) + data curation + Avalon fingerprints using the RDKit fingerprints node available in the KNIME

* **Approach:**
  * Developed multitask DNN models utilising the multilayer feedforward neural networks implemented in Keras using the Tensorflow backend
  * The loss function was minimised using the Adam algorithm
  * To further identify the best hyperparameters for DNN, they used the grid search function available from the scikit-learn library
  * In this study, the single-task regression models (ST-RF) were built using the RF implementation in scikitlearn. The number of trees was arbitrarily set to 100 since it has been shown that the optimal number of trees is usually 64−128, while further increasing the number of trees does not necessarily improve the model’s performance. Due to the robust nature of RF no parameter optimisation was performed

* **Model performance:**
  * Model comparison with other existing models
  * 5-fold cross-validation procedure
  * Root-mean-squared error (RMSE) and determination coefficient R<sup>2</sup>
  * The statistical significance as p-value was defined less than 0.05

* **Applicability domain:**
  * (1) Tanimoto similarity between the test set compounds and nearest neighbor in the training set using Morgan fingerprints
  * (2) Extracted the prediction output for each compound from individual descriptor models and calculated the standard deviation (SD) of prediction for each compound. Then, for each end point, the mean (μ) and standard deviation (σ) from the standard deviation of prediction for each compound was calculated. They then filtered out those compounds that were above the μ + 0.5 σ (t1), μ + σ (t2), μ + 2σ (t3), and μ + 3σ (t4) simultaneously and calculated the RMSE and coverage on the remaining.
  * In addition to “random split”, they also performed “scaffold split”, which is challenging but a more realistic evaluation of the predictive power of the models

* **Key learnings:**
  * The best results were obtained from the consensus of the predictions from multitask DNN, GCNN, and DLCA models
  * MT-DNN approach offers a statistically significant advantage over single-task models, especially for end points with smaller number of compounds
