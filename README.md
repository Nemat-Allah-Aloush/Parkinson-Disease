# Parkinson-Disease

## Index
2. [Dataset description](#2-dataset-description)
4. [Motif Search](#4motif-search)
6. [Classification](#6classification)
7. [Clustering](#7clustering)
9. [SVM models on extracted features](#9svm-models-on-extracted-features)
10. [Models on sequence data](#10models-on-sequence-data)
11. [Interpretation](#11interpretation)
12. [Applying FWHM scaling and adding other features for RFC](#12applying-fwhm-scaling-and-adding-other-features-for-rfc)
13. [Statical base model on filtered data](#13statical-base-model-on-filtered-data)
14. [DataClass](#14dataclass)
15. [RFClassifier](#15rfclassifier)
16. [RFC models](#16rfc-models)
18. [Explinable Models](#18explinable-models)
19. [The Hybrid models](#19the-hybrid-models)
----

### 2. Dataset Description

For the later tasks, the following data set was used.
The database contains measures of gait from 93 patients with idiopathic PD, and 73 healthy controls.
The dataset contains:
1. Vertical ground reaction force records of subjects as they walked for approximately 2 minutes
on level ground.

  • The file contains the measures from 8 sensors for each foot.

  • Each individual walks for 2 minutes, records are taken at 100 samples per second.

  Thus, we have 12000 record for each 2 mins walk.

2. Demographics file contains demographic information, measures of disease severity and other
related measures.



### [4.Motif Search](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/Motif%20Search)

In the [first](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Motif%20Search/Motif_Search.ipynb) file, tried to apply motif identification on different features from the time series dataset, it appeared that the shape of the dataset (pressure - no pressure) is what resulted as motif and that is not useful.

In the [second](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Motif%20Search/Motif_Search_with_filtering.ipynb) file, Tried to filter the data, but still having the same problem.


 
### [6.Classification](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Classification.ipynb)

| Task                       | features                               | Accuracy      |
| -------------              | -------------                          | ------------- |
| Severity Detection         | Univariate classification (L2 sensor)  | 0.39          |
| Parkinson’s Classification | Univariate classification (L2 sensor)  | 0.71          |
| Severity Detection         | Multivariate classification            | 0.38          |
| Parkinson’s Classification | Multivariate classification            | 0.82          |

### [7.Clustering](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/Clustering)

Clustering for fait time series dataset did not result in promising results. 
The [first](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Clustering/Clustering_PD_VGF_Gait_Stances.ipynb) file tried to cluster the data from both lef and right feet. The [second](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Clustering/Clustering_left_stances.ipynb) file applies the clustering on data from the left foot only. The [third](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Clustering/Clustering_right_stances.ipynb) file applies the clustering on data from the right foot only.



### [9.SVM models on extracted features](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/SVM%20models_%20extracted%20features.ipynb)

Data Class + Applying FWHM on accumalated forces fro the right foot + applying SVM models on features extracted from the sequences.


### [10.Models on sequence data](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Models_Sequences_data.ipynb)

Data Class + Applying FWHM on accumalated forces fro the right foot + applying models on the sequences.

### [11.Interpretation](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Interpretation.ipynb)
Interpretation for the features RF Classifier with 100 estimator on scaled stances that resulted with 0.94 accuracy.

### [12.Applying FWHM scaling and adding other features for RFC](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/fwhm_scaling_RFC.ipynb)
Applying FWHM scaling and adding other features (stride time, max heel strike, max toe strike) for RFCs

### [13.Statical base model on filtered data](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Revisit_statical_models.ipynb)

Applying random forest classifier on the statics from the raw signal data AFTER being filtered.

### [14.DataClass](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/DataClass)

The dataclass contains read the data, segment it, scale it and iterpolate it.

### [15.RFClassifier](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/RFClassifier)

Class for training, predicting, scoring the results with Random Forest Classifier.

### [16.RFC models](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/RFCmodels.ipynb)
In this code file, we use [class data](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/DataClass) and [RFC class](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/RFClassifier) to apply the previous different models on the data.
(SUMMING UP)
1. RFC basemodel using statics from raw data.
2. RFC models on interpolated scaled stances with FWHM algorithm, and additional features
3. RFC on scaled stances with 3 extra features and statics
4. RFC on scaled stances with 6 extra features and statics
5. RFC model on scaled stances from the right & left foot with 6 extra features each
6. RFC model on scaled stances from the right & left foot with 6 extra features each and basemodels
7. RFC model on scaled stances from 16 sensor from the right & left foot with 6 extra features each
8. RFC model on scaled stances from 16 sensor from the right & left foot with the sum of all sensors and with 6 extra features each
9. RFC model on scaled stances from 16 sensor from the right & left foot and the sum of all sensors and with 6 extra features each foot and the statics from base models

| Model                      | Input data                                                    | Accuracy      | Precision      | Recall      | F1      |
| -------------              | -------------                                                 | ------------ | ------------ | ------------ | ------------ |
| RFC n_est=100, Rand=42     | Statics on filtered raw data from each sensor  | 0.921  |0.9167 |0.9821          |0.9483          |
| RFC n_est=100, Rand=42     | Right foot related: [ Interpolated Scaled stances, 3 features]  | 0.9418 |0.9370  |0.9803 |0.9581 |
| RFC n_est=100, Rand=42     | Right foot related: [ Interpolated Scaled stances, 6 features]| 0.9537|0.9461 |0.9880|0.9666|


### [18.Explinable Models](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/Explaining)
[First file](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Explaining/Explinability.ipynb): Finding what features are more important on models trained on statics and extracted features

[Second file](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Explaining/Explinability_Continue.ipynb): Showing the most important features in different plots.

### [19.The Hybrid models](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/Hybrid_Models)
1.[Trying hybrid models](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Hybridmodel.ipynb)
trying different hybrid models for right stances and 3 features.

2.[Hybrid model](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Hybridmodels.ipynb)
Hybrid model class and a train it on for right stances and 3 features and on for right stances and 6 features.

Two final notebooks for training hybrid model on all data with/without statics for binary classification and severity Detection. 

----
References:
[1] G. Gilmore, A. Gouelle, M. B. Adamson, M. Pieterman, and M. Jog, “Forward and backward walking in Parkinson disease: A factor analysis,” Gait & Posture, vol. 74, pp. 14–19, Oct. 2019, doi: 10.1016/J.GAITPOST.2019.08.005.
