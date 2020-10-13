## 2020 DIGIX GLOBAL AI CHALLENGE: Advertisement CTR prediction

A submission for  [HUAWEI - 2020 DIGIX GLOBAL AI CHALLENGE](https://developer.huawei.com/consumer/en/activity/devStarAI/algo/competition.html#/preliminary/info/digix-trail-03/introduction)

**team** Melbourne dağları  
**members:** [@mustafahakkoz](https://github.com/mustafahakkoz), [@Aysenuryilmazz](https://github.com/Aysenuryilmazz)  
**rank:** 94/ 343  
**score (AUC):** 0.679876  
**dataset:** [advertising behavior data](https://developer.huawei.com/consumer/en/activity/devStarAI/algo/competition.html#/preliminary/info/digix-trail-03/data) Heavily unbalanced and very large / out of core dataset containing the advertising behavior data collected from seven consecutive days. 

- training dataset (6.09 GB, 43M rows, 36 cols)

- 2 testing datasets (153 MB, 1M rows, 36 cols) 

---

#### Idea:

The main ideas of the project are:

1. Reading dataset with chunks and downcasting to fit into the memory.

2. Target encoding with smoothing.

3. SGD model with mini-batches.

4. class_weights to balance classes.

Implementation details can be found in the document [DIGIX Implementation Instruction.docx](https://github.com/mustafahakkoz/Advertisement-CTR-Prediction/blob/master/DIGIX%20Implementation%20Instruction.docx "DIGIX Implementation Instruction.docx").

---

#### Repo Content and Implementation:

[1. read data](https://github.com/mustafahakkoz/Advertisement-CTR-Prediction/tree/master/1.%20read%20data "1. read data") 

- We read whole train (42M) dataset with chunk size of 10K and apply downcast to reduce the size in memory.

[2. target encoding with smoothing](https://github.com/mustafahakkoz/Advertisement-CTR-Prediction/tree/master/2.%20target%20encoding%20with%20smoothing "2. target encoding with smoothing") 

- We implemented target encoding on columns by using a custom function which smooths standard target encoding with global mean of a column.

- We dropped uid and pt_d columns on train dataset.

- We shuffle the dataset and split it to 40M for train and rest (~2M) for test purposes.

- We produce train dataset in several notebooks due to hard disk limitations of Kaggle platform (only 5GB).

[3. SGD with class_weight](https://github.com/mustafahakkoz/Advertisement-CTR-Prediction/tree/master/3.%20SGD%20with%20class_weight "3. SGD with class_weight")

- We chose SGD model of Scikit Learn with default parameters and feed it with batches of 10K.

- For every batch we used class_weight parameter to balance classes.

- After evaluating our model on our test dataset (with AUC score of 70%), we refit our model on whole training set (~42M) and export the model.

[4. prediction and submission](https://github.com/mustafahakkoz/Advertisement-CTR-Prediction/tree/master/4.%20prediction%20and%20submission "4. prediction and submission")

- By using exported model, we implement prediction on submission dataset test_data_B.csv. For this step we used mean values to fill NA values which are produced by target encoding because of newly encountered values.

---

#### Notes:

- We didn’t use any cross validation or hyper parameter tuning technique for this contest due to computational constraints of online platforms.

- We didn’t perform any of feature engineering techniques also.

- We also tried Decision Tree, XGBoost, catboost and lightGBM with several parameters but they didn’t work out due to memory errors.

- This repo only contains of final versions. Experiments are implemented in kaggle platform. All of the notebooks including scratches also can be found in [this kaggle link](https://www.kaggle.com/hakkoz/notebooks) with `CTR` tag.


