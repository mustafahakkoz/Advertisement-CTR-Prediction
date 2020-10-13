## 2020 DIGIX GLOBAL AI CHALLENGE: Advertisement CTR prediction

A submission for  [HUAWEI - 2020 DIGIX GLOBAL AI CHALLENGE](https://developer.huawei.com/consumer/en/activity/devStarAI/algo/competition.html#/preliminary/info/digix-trail-03/introduction)

**team** Melbourne dağları  
**members:** [@mustafahakkoz](https://github.com/mustafahakkoz), [@Aysenuryilmazz](https://github.com/Aysenuryilmazz)  
**rank:** 94/ 343  
**score (AUC):** 0.1564  
**dataset:** [advertising behavior data](https://developer.huawei.com/consumer/en/activity/devStarAI/algo/competition.html#/preliminary/info/digix-trail-03/data) Heavily unbalanced and very large / out of core dataset containing the advertising behavior data collected from seven consecutive days. 

- training dataset (6.09 GB, 43M rows, 36 cols)

- 2 testing datasets (153 MB, 1M rows, 36 cols) 

---

The main idea of the project is:

1. Reading dataset with chunks and downcasting to fit into the memory.

2. Target encoding with smoothing.

3. SGD model with mini-batches.

4. class_weights to balance classes.

This repo only contains of final versions. Experiments are implemented in kaggle platform. All of the notebooks including scratches also can be found in [this kaggle link](https://www.kaggle.com/hakkoz/notebooks) with <CTR> tag.

#### FOLDER CONTENT

- **Processing datasets and to images with 3 methods defined above:** This code also produces predictions without ML, just by counting contours. [process_videos.py](https://github.com/mustafahakkoz/ALZHEIMER-contest/blob/master/process_videos.py)  
- **CNN predictor:** [CNN.py](https://github.com/mustafahakkoz/ALZHEIMER-contest/blob/master/CNN.py)  
- **Submission format for no-ML predictions:** [submission_format_no_ml.py](https://github.com/mustafahakkoz/ALZHEIMER-contest/blob/master/submission_format_no_ml.py) 
