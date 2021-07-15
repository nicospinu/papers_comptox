* https://doi.org/10.1038/s42004-021-00528-9

* **Background:**
  * With the vast amount of chemicals in use today, it is not possible to determine experimental values for all of them
  * Chemicals that are of interest today such as ionizable chemicals, and chemicals with many functional groups were often not included in the development of the models or sometimes cannot be represented by the used substance descriptors or indices
  * Simply excluding outliers without proper cause is strictly discouraged, since this would lead to overfitting and decrease the reliability of the prediction

* **Aim:** 
  * Establish a DNN model which allows highly accurate predictions of log P within a broad application domain

* **Data:** 
  * logP values and SMILES
  * As molecular input we use convoluted graphs, since their use has proven very effective to predict molecular properties and activities
  * Data augmentation by inclusion of all potential tautomers of a chemical to improve the predictions
  * Different SMILES representations for each chemical (original SMILES, canonical SMILES, and SMILES with explicit Hs) as well as potential tautomers represented as SMILES codes, which were generated with JChem, were used for handling the data
  * 10 % test set + 90 % model development (80% training set, and 20% validation set)
  * The test set was used to evaluate the overall performance of the selected DNN models
  * The validation set was used for the optimization of the DNN models and to select the best DNN out of all trained DNN models
  * pKa and pKb values were calculated for all chemicals by two models of ACD Percepta and JChem for Excel SMILES of the chemicals were converted into graphs (ConvMolFeaturizer) and used as features

* **Approach:**
  * Two DNN models developed: original SMILES and the data augmentation SMILES
  * DNN models were developed using the DeepChem library and Tensorflow
  * Tools for comparison: associated neural networks (OCHEM, ALOGPS), fragmental or atom-based methods (KOWWIN, ACD/GALAS, JChem, DataWarrior), and a quantum-chemistry-based calculation (COSMO-RS)
  * The strategy was developing DNN models to screen for outliers by comparing the predicted and experimental log P values

* **Model development:**
  * The feed-forward network consists of two hidden layers with 64, and 128 neurons, which were connected to a dense layer (with ReLU activation function) followed by batch normalization (including a dropout of 0.1) and the output layer (with tanh activation function)
  * Each hidden layer was constructed by a graph convolution, a batch normalization and a graph pool layer. The DNNmono and DNNtaut were trained for 70 and 60 epochs respectively, with a batch size of 50 and the learning rate was set to 0.00005 and 0.0001, respectively
  * These parameters were optimized first by evaluation of the outcomes for the validation set

* **Identification of errors in the dataset:**
  * Two potential sources of error can occur for a data point in the dataset: (A) the chemical structure is not mapped correctly or (B) the corresponding value (in our case log P) is wrong
  * In case (A), false representations of the real structure are caused either by a nomenclature error in the primary source or by a wrong assignment of identifiers, such as CAS number or SMILES
  * For case (B), we could identify several issues in the dataset: we found mismatches in the values given in the dataset and the ones in the primary source. This is caused by transcription errors and wrong conversions (e.g., calculation of log P from a chromatographic capacity factor), and by the wrong assignment of experimental log P values for a chemical, where different log P values are given
  *They also identified duplicates in the dataset resulting from different structural representations of the same compound, and it is often not clear which criteria should be used to select the correct value. Tautomers can generate this problem but also salts
  * No difference should occur if the corresponding pH values were selected correctly for both variants during the measurement of the log P value. In this case we kept the neutral form of the chemical in the dataset and excluded the salt
  * If the log P value is determined for ionizable chemicals, differences in the values for the neutral and ionic species are expected, and the log P values depend on the given pH in the experimental system. For ionizable chemicals (under consideration of the fractions fspecies, pH of all possible species at a given pH value), the octanol–water partition coefficient D can be defined as follows: log D = log ΣPspecies*fspecies,pH. An ideal model would predict log D instead of log P for a given pH value under consideration of all possible speciations of the molecule

* **Model performance:**
  * RMSE

* **Key learnings:**
  * Best prediction performance was achieved by DNN based on the augmented data
  * Analyzing the dataset and developing the models, it becomes apparent that the overall performance is extremely dependent on the quality of the dataset and necessary additional information (e.g., pH conditions of log P measurement)
  * Models based on an extended dataset with log D values for different ionic species of a chemical would provide more precise predictions 
  * An included, improved prediction of the pKa and pKb values for the chemicals would be necessary
  * The data augmentation applied here, which uses all possible tautomers in the training, should further be the best way to handle tautomers because the necessary log P values for the respective tautomer forms are not available
  * DNN model development based on chemical datasets needs a lot of expertise and intensive analysis of the dataset itself even if the dataset is highly curated
