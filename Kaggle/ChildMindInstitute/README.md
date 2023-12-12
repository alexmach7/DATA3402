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
* Removed false sleep and onset from when the accelerometer was removed.
## Data Visualization
![image](https://github.com/alexmach7/DATA3402/assets/113038988/483fb552-38e0-432c-a972-929d5b88ff05)
05e1944c3818
![image](https://github.com/alexmach7/DATA3402/assets/113038988/43ecb644-178d-4b0e-afe6-254998c72f8b)
04f547b8017d
![image](https://github.com/alexmach7/DATA3402/assets/113038988/321200f1-db25-4357-834b-721915b9e7a2)
0402a003dae9
![image](https://github.com/alexmach7/DATA3402/assets/113038988/ae3301d9-796e-401b-8a2d-4dbb592b24ae)
03d92c9f6f8a
![image](https://github.com/alexmach7/DATA3402/assets/113038988/fba222a4-6e5d-4bf4-b19c-97efb48c880e)
038441c925bb

