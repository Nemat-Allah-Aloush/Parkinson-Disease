# Parkinson-Disease

## Index
1. [Forward and Backward walking in PD ON_OFF Medication](#1.-forward-and-backward-walking-in-pd-on_off-medication)
2. [Dataset description](#2.-Dataset-Description)
3. [Statical Base Models](#3.-Statical-Base-Models)
----

### [1. Forward and Backward walking in PD ON_OFF Medication](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/tree/main/Forward%20and%20Backward%20walking%20in%20PD%20ON_OFF%20Medication)  
Data analysis for gait dataset[1] collected from Parkinspn's dissease patients.

The dataset can be found by following the link, [here](https://data.mendeley.com/datasets/7t658vpdhj/1/files/27c3a522-8baa-4ffd-8547-5f3b4ca240f6).

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

### [3. Statical Base Models](https://github.com/Nemat-Allah-Aloush/Parkinson-Disease/blob/main/Statical%20base%20models.ipynb)

In this file statics for each sensor measures (avg, min, max, median, standard deviation, skewness, kvrtosis) were calculated.
1. Trained a simple SVC, or Support Vector Classifier to classify PD and healthy subjects and got 0.79 test accuracy.
2. Trained a KNN, when getting a good training accuracy, the model was overfitted.

When training with Neighbors = 15

Accuracy on training set: 0.83 Accuracy on test set: 0.82

Precision: 0.82 Recall: 0.92 F1: 0.87
3. Trained Random Forest Classifier.

When training with estimators = 200, got tests accuracy = 0.97.

----
References:
[1] G. Gilmore, A. Gouelle, M. B. Adamson, M. Pieterman, and M. Jog, “Forward and backward walking in Parkinson disease: A factor analysis,” Gait & Posture, vol. 74, pp. 14–19, Oct. 2019, doi: 10.1016/J.GAITPOST.2019.08.005.
