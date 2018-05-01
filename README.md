# toxic-comment-detector

Discussing things you care about can be difficult. The threat of abuse and harassment online means that many people stop expressing themselves and give up on seeking different opinions. Platforms struggle to effectively facilitate conversations, leading many communities to limit or completely shut down user comments. What we are trying to accomplish here is to create an automated tool keep such uncouth activities in control.

## General links:
- Kaggle Competition: [Link][1]
- ConversationAI: [Link][2]


## Approaches explored:
- NBSVM (Baseline) : [Link][5]
- XGBoost: [Link][3]
- LightGBM: [Link][4]
- Feed-forward Neural Network with embeddings layer (DNN): [Link][10]
- CNN: [Link][6]
- CNN with Pre-trained embeddings (CNN PR-EMB): [Link][9]
- LSTM: [Link][7]
- Bi-Directional LSTM (BDLSTM): [Link][8]

## Common Rules across all the models:
- Vocabulary size = 6500
- Maximum sentence size = 400
- Embedding Size = 50
- Train one time for multi-class classification and not 6 times for binary classification
- Therefore, we will get one test set AUC (and its standard deviation) from each model
- To get standard deviation, use either 10-fold cross validation OR run the experiment 10 times
- first 80% train set, last 20% test set

## Results so far:

|                   | Test Set AUC | Std. Dev. | Status               |
|:-----------------:|--------------|-----------|----------------------|
| Linear Classifier | 0.9059       | 0.033     |                      |
| NBSVM (Baseline)  | 0.9199       | ??        | (needs confirmation) |
| XGBoost           | 0.5          | ??        | (needs confirmation) |
| LightGBM          | 0.95         | ??        | (needs confirmation) |
| DNN               | 0.8958       | 0.0756    |                      |
| CNN               |              |           | (still running)      |
| CNN PR-EMB        | 0.9104       | 0.0365    |                      |
| LSTM              |              |           | (still running)      |
| BD LSTM           | 0.98         | ??        | (needs confirmation) |


[1]: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge
[2]: https://conversationai.github.io/
[3]: ../XGBOOST/README.md
[4]: ../light-gbm/README.md
[5]: ../baseline/NBSVM.ipynb
[6]: ../djksf
[7]: ../sajfud
[8]: ../sajkhjfd
[9]: ../dsaif
[10]: ../sajif