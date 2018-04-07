# toxic-comment-detector

Discussing things you care about can be difficult. The threat of abuse and harassment online means that many people stop expressing themselves and give up on seeking different opinions. Platforms struggle to effectively facilitate conversations, leading many communities to limit or completely shut down user comments. What we are trying to accomplish here is to create an automated tool keep such uncouth activities in control.

## General links:
- Kaggle Competition: [Link][1]
- ConversationAI: [Link][2]


## Approaches explored:
- XGBoost: [Link][3]
- LightGBM: [Link][4]
- NBSVM (Baseline) : [Link][5]

[1]: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge
[2]: https://conversationai.github.io/
[3]: ../XGBoost/README.md
[4]: ../light-gbm/README.md
[5]: ../baseline/NBSVM.ipynb

## LightGBM
### Why lightGBM?
1. Faster training speed and higher efficiency: Light GBM use histogram based algorithm i.e it buckets continuous feature values into discrete bins which fasten the training procedure.
2. Lower memory usage: Replaces continuous values to discrete bins which result in lower memory usage.
3. Better accuracy than any other boosting algorithm: It produces much more complex trees by following leaf wise split approach rather than a level-wise approach which is the main factor in achieving higher accuracy. However, it can sometimes lead to overfitting which can be avoided by setting the max_depth parameter.
4. Compatibility with Large Datasets: It is capable of performing equally good with large datasets with a significant reduction in training time as compared to XGBOOST.
5. Parallel learning supported.


### Parameters we have looked at till now
1. Control Parameters
* feature_fraction: Used when your boosting(discussed later) is random forest. 0.8 feature fraction means LightGBM will select 80% of parameters randomly in each iteration for building trees.
* bagging_fraction: specifies the fraction of data to be used for each iteration and is generally used to speed up the training and avoid overfitting.
* lambda: lambda specifies regularization. Typical value ranges from 0 to 1.

2. Core Parameters
* learning_rate: This determines the impact of each tree on the final outcome. GBM works by starting with an initial estimate which is updated using the output of each tree. The learning parameter controls the magnitude of this change in the estimates. Typical values: 0.1, 0.001, 0.003…
* num_leaves: number of leaves in full tree, default: 31
* application: This is the most important parameter and specifies the application of your model, whether it is a regression problem or classification problem. LightGBM will by default consider model as a regression model. regression: for regression; binary: for binary classification; multiclass: for multiclass classification problem
* num_boost_round: Number of boosting iterations, typically 100+

3. Metric Parameters
* metric: again one of the important parameter as it specifies loss for model building. Below are few general losses for regression and classification.
mae: mean absolute error; mse: mean squared error; binary_logloss: loss for binary classification; multi_logloss: loss for multi classification


### Other Parameters to look at
1. Control Parameters
* max_depth: It describes the maximum depth of tree. This parameter is used to handle model overfitting. Anytime the model looks like it is overfitting, try to lower max_depth.
* min_data_in_leaf: It is the minimum number of the records a leaf may have. The default value is 20, optimum value. It is also used to deal over fitting
* early_stopping_round: This parameter can help you speed up your analysis. Model will stop training if one metric of one validation data doesn’t improve in last early_stopping_round rounds. This will reduce excessive iterations.
* min_gain_to_split: This parameter will describe the minimum gain to make a split. It can used to control number of useful splits in tree.
* max_cat_group: When the number of category is large, finding the split point on it is easily over-fitting. So LightGBM merges them into ‘max_cat_group’ groups, and finds the split points on the group boundaries, default:64

2. Core Parameters
* boosting: defines the type of algorithm you want to run, default=gdbt
gbdt: traditional Gradient Boosting Decision Tree; rf: random forest; dart: Dropouts meet Multiple Additive Regression Trees; goss: Gradient-based One-Side Sampling
* device: default: cpu, can also pass gpu

3. I/O Parameters
* max_bin: it denotes the maximum number of bin that feature value will bucket in.
* categorical_feature: It denotes the index of categorical features. If categorical_features=0,1,2 then column 0, column 1 and column 2 are categorical variables.
* ignore_column: same as categorical_features just instead of considering specific columns as categorical, it will completely ignore them.
* save_binary: If you are really dealing with the memory size of your data file then specify this parameter as ‘True’. Specifying parameter true will save the dataset to binary file, this binary file will speed your data reading time for the next time.


### More on the LightGBM Approach:
1. [lightGBM vs XGBoost - Analytics Vidhya](https://www.analyticsvidhya.com/blog/2017/06/which-algorithm-takes-the-crown-light-gbm-vs-xgboost/)
2. [Medium - what is lightgbm and how to implement it](https://medium.com/@pushkarmandot/https-medium-com-pushkarmandot-what-is-lightgbm-how-to-implement-it-how-to-fine-tune-the-parameters-60347819b7fc)
