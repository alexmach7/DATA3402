# Child Mind Institute - Detect Sleep States
* This repository holds an attempt to apply LSTMs to accelerometer data from "Detect Sleep States" Kaggle challenge.
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
* Randomly selected 40 patients to study. Removed NaN values and aligned 'series_id', 'enmo', 'anglez', and 'event' using 'timestamp'.
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
* Clearly define the key performance metrics
![image](https://github.com/alexmach7/DATA3402/assets/113038988/db5fcf8f-dff9-4753-8ce3-57cb3b39b17b)


* show visualizations, ROC curve

## Conclusions
* example LSTM worked better than GRU

## Future Work
* what is the next thing I would like to try
* What are some other studies that can be done starting from here

# How to reproduce results
## Overview of files in repository
 * Directory stucture
 * relevant files and thier role
     * train_series.parquet - Series to be used as training data. Each series is a continuous recording of accelerometer data for a single subject spanning many days.
     * test_series.parquet - Series to be used as the test data, containing the same fields as above. You will predict event occurrences for series in this file.
     * train_events.csv - Sleep logs for series in the training set recording onset and wake events.
     * sample_submission.csv - A sample submission file in the correct format.
## Software Setup
* list required packages
## Data
* where to download data
## Training
* describe how to train the model
