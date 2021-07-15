* https://doi.org/10.1021/acs.chemrestox.0c00347

* **Background:** 
  * As an idiosyncratic ADR, drug-induced rhabdomyolysis (DIR) is rare but lethal in clinics. Limited methods in clinics, such as monitoring CK values, make it difficult to diagnose DIR effectively, which makes the early detection of DIR very arduous. because of the scarcity of DIR cases and the lack of negative drugs, to our best knowledge, the performance of the models was still suboptimal and can be improved by using a well-defined DIR data set

* **Aim:** 
  * Random forest (RF) model to predict the DIR severity of the marketed drugs based on the chemical structure information

* **Data type:** 
  * A prevous developed data repository of 213 drugs based on the FDA drug labeling content plus Mold2 descriptors
  * Extracted 1402 drugs from the FAERS database, which had been reported to cause DIR to varying degrees, and applied the RF model to detect the drugs with serious DIR (validation set)

* **Data curation:**
  * Removed the descriptors with a variance less than 0.001

* **Approaches:**
  * Random forest
  * Two parameters, namely, the number of trees and the maximum depth of the DT, were optimized by a grid search approach
  * A drug with a predicted probability higher than 0.5 was considered a high-risk DIR drug
  * Model comparison against permutation tests and 3 MLs used the Mann Whiney U test to indicate the significance of the difference between the prediction results of the RF model and the other models
  * After selecting the best parameters, to obtain a statistically robust estimation of model performance, the modeling procedures were conducted 1000 times. At same time, we conducted two permutation tests. One is the DIR labels for the drugs were randomly permuted to generate a permutated labels data set, and the other is the features of the drugs that were randomly permuted to generate a permutated features data set. On the basis of the permutated labels data set and the permutated features data set, the RF models were also constructed by 1000 iterations of 5-fold cross-validations, respectively. Compared with the performance of the models in the two types of permutation tests, we can estimate whether the performance of the models with the real data set was really better than that of the random models
  * Extreme gradient boosting (XGBoost), the minimum loss reduction parameter (γ) and the maximum depth of a tree were determined by using the training set
  * Support vector machine (SVM), used the radial basic function (RBF) as the kernel function and estimated the regularization parameter (c) and kernel width (γ) in the modelling procedure
  * Logistic regression (LR) were involved to predict the DIR severity. estimated the inverse of regularization strength (C) in the model training procedure

* **Model performance:**
  * Accuracy, recall rate, precision, Matthews correlation coefficient (MCC), balance accuracy (BACC), F1 score, area under the receiver operating characteristic curve (AUROC), area under the precision-recall curve (AUPRC) , and specificity
  * Used the average metrics of 1000 iterations of 5-fold cross-validations to evaluate the model performance

* **Key learnings:**
  * Outperformed extreme gradient boosting, support vector machine, and logistic regression
  * Showing the applicability: In the study of a real application, the RF model was applied to predicting the potentially serious DIR of 1402 drugs, which were reported to cause DIR by FAERS
  * The RF model performed the best among all the models
  * The current model was sensitive to detect the drugs in the specific therapeutic categories
