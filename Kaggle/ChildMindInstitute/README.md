# Child Mind Institute - Detect Sleep States
* This repository holds an attempt to apply Decision Trees to accelerometer data from "Detect Sleep States" Kaggle challenge.
* https://www.kaggle.com/competitions/child-mind-institute-detect-sleep-states/overview
## Overview
* The task, as defined by the Kaggle challenge is to use time series of multi-day recordings to conduct more reliable sleep studies.
## Summary of Workdone
### Data
* Data:
  * Type:
    * Input: multi-day recordings of wrist-worn accelerometer data annotaed with onset and wakeup. Parquet file: train_series.parquet
    * Size: 986.46 MB
    * Instances: 500 multi-day recordings, roughly as many nights recorded for a series as there are 24-hour periods in that series.
## Processing/Clean up
* Randomly selected 40 patients to study. Removed false data from when the accelerometer was removed. Aligned 'series_id', 'enmo', 'anglez', and 'event' using 'timestamp'.
## Data Visualization
### Comparing Series
![image](https://github.com/alexmach7/DATA3402/assets/113038988/483fb552-38e0-432c-a972-929d5b88ff05)
Series ID: 05e1944c3818
![image](https://github.com/alexmach7/DATA3402/assets/113038988/43ecb644-178d-4b0e-afe6-254998c72f8b)
Series ID: 04f547b8017d
![image](https://github.com/alexmach7/DATA3402/assets/113038988/321200f1-db25-4357-834b-721915b9e7a2)
Series ID: 0402a003dae9
![image](https://github.com/alexmach7/DATA3402/assets/113038988/ae3301d9-796e-401b-8a2d-4dbb592b24ae)
Series ID: 03d92c9f6f8a
![image](https://github.com/alexmach7/DATA3402/assets/113038988/fba222a4-6e5d-4bf4-b19c-97efb48c880e)
Series ID: 038441c925bb
## Problem Formulation
* Define
  * Input
    * series_id - Unique identifier for each accelerometer series.
    * timestamp - A corresponding datetime.
    * anglez - As calculated and described by the GGIR package, z-angle is a metric derived from individual accelerometer components that is commonly used in sleep detection, and refers to the angle of the arm relative to the vertical axis of the body.
    * enmo - Euclidean Norm Minus One of all accelerometer signals, with negative values rounded to zero.

## Training
* I trained with a Decision Tree.
* The area under the ROC curve was 0.54.
* I spent a lot of time preparing my data but wish I could have focused more on training.

## Performance Comparison
* Accuracy = (Number of Correct Predictions) / (Total Number of Predictions)
* Precision = (True Positives) / (True Positives + False Positives)
* Recall = (True Positives) / (True Positives + False Negatives)
* F1 Score = 2 * ((Precision * Recall) / (Precision + Recall))
* The ROC curve is created by plotting the true positive rate on the y-axis against the false positive rate on the x-axis for different threshold values.
![image](https://github.com/alexmach7/DATA3402/assets/113038988/db5fcf8f-dff9-4753-8ce3-57cb3b39b17b)
![image](https://github.com/alexmach7/DATA3402/assets/113038988/045b44c6-868c-45f9-a131-a9603f262e33)


## Conclusions
* I chose a simple model but it was still close to accurate.

## Future Work
* In the future I would like to compare more training models. I also only chose 40 patients to study because I was having trouble with my computer crashing. If I had been able to I would have liked to have a larger sample size. 

# How to reproduce results
## Overview of files in repository
 * Relevant files:
     * train_series.parquet - Series to be used as training data. Each series is a continuous recording of accelerometer data for a single subject spanning many days.
     * test_series.parquet - Series to be used as the test data, containing the same fields as above. You will predict event occurrences for series in this file.
     * train_events.csv - Sleep logs for series in the training set recording onset and wake events.
     * sample_submission.csv - A sample submission file in the correct format.
## Software Setup
### Packages Needed
* from pathlib import Path
* import pyarrow.parquet as pq
* import gc
* import seaborn as sns
* import matplotlib.pyplot as plt
* import random
* import pandas as pd
* from sklearn.preprocessing import LabelEncoder
* from sklearn.model_selection import train_test_split
* from sklearn.tree import DecisionTreeClassifier
* from sklearn.metrics import accuracy_score, classification_report
* from sklearn.metrics import roc_curve, roc_auc_score
## Data
* Download data at: https://www.kaggle.com/competitions/child-mind-institute-detect-sleep-states/data
## Training
X = merged_data[['enmo', 'anglez']]  
y = merged_data['event']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = DecisionTreeClassifier()

model.fit(X_train, y_train)
