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
* removed false sleep and onset from when the accelerometer was removed
