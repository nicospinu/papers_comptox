* https://doi.org/10.1021/acs.chemrestox.0c00423

* **Background:** 
  * DILI adverse reactions is either intrinsic dose dependent toxicity or idiosyncratic as a result of the adaptive immune system (reactive metabolites, mitochondrial toxicity etc.)
  * Many reasons of failure to translate animal data to humans including the P450 metabolism path

* **Aim:** 
  * Development of a battery of QSAR models for binary classification of DILI based on molecular descriptors for two datasets (human evidence derived and mammalian data) and metabolism knowledge including species-differentiating structural features analysis and uncertainty quantification using DST

* **Data type:** 
  * Set A: oral marketing pharmaceuticals (human DILI evidence)
  * Set B: pre-clinical mammalian repeated dose toxicity studies from regulatory sources for both pharmaceuticals and non-pharmaceuticals
  * Set C: metabolism data for pharmaceuticals
  * Set D: external validation set (65 compounds for hDILI and 41 compounds for mammalian DILI)

* **Data curation:**
  * InChI key used to check for duplicates
  * Neutralisation of charged structures using CORINA Symphony
  * Both 2D and 3D forms were generated to calculate molecular descriptors
  * Several molecular descriptors were selected and calculated in CORINA Symphony
  * The reduction of descriptors space was done with partial least-squares (PLS) regression technique

* **Approaches:**
  * Structural rules were designed using the ToxPrint chemotypes in ChemoTyper
  * An ensemble approach of learning algorithms was used composed of: Artificial neural network, k-Nearest Neighbors, Logistic regression, random forest, support vector machine
  * ANN used 1 hidden layer with 21 neurons
  * Logistic regression regularization parameter was 0.1
  * SVM used a regularisation parameter of 4.3 and the radial basis function kernel
  * KNN used 9 neighbours
  * RF used 25 or fewer leaf nodes and a maximum depth of 12
  * Dempster−Shafer decision theory used to combine multiple sources of evidence (i.e., predictions from QSAR models and structural rules) and to estimate the uncertainty associated with each predicted outcome
  * Selected ToxPrint chemotypes were checked to understand differences of human vs mammalian *in vivo* studies based on z-score and grouped into four groups: (1) positively associated with hDILI and mHepTox, (2) negatively associated with both end points, (3) positive in hDILI but negative in mHepTox, and (4) negative in hDILI but positive in mHepTox. These latter discordant features were used as building blocks to define structural rules for differentiating human results from those for the combined mammalian group
  * Separate QSAR models were developed for each endpoint (oral hDILI and mammalian DILI)

* **Model performance:** 
  * Accuracy, balanced accuracy, specificity, sensitivity, positive predictive value, negative predictive value, Matthews correlation coefficients
  * A k-fold cross-validation scheme is employed to construct models and provide a reasonable estimate of the expected error on predictions for external data sets

* **Key learnings:**
  * If the predictions are discordant, both metabolites and parents are investigated for quantitative structure−activity relationship and species-differentiating chemotypes
  * The results are combined using the Dempster−Shafer decision theory to yield a final outcome prediction for human DILI with estimated uncertainty
  * A key feature of DST is that the reliability of each source is rigorously taken into account; for example, a WOE result obtained by combining the prediction from an ensemble of QSAR models with predictions from a structural rule gives more weight to the more accurate approach, as determined from validating the performance of each against a known test set
  * Metabolic differentiation between species may be explored from the structural rule-based perspective
  * SVM, ANN, and k-NN models were further selected as the best overall performers when combining to obtain an ensemble prediction
  * The external validation resulted in lower specificity, whereas the sensitivity was much better
