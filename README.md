# toxic-comment-detector

Discussing things you care about can be difficult. The threat of abuse and harassment online means that many people stop expressing themselves and give up on seeking different opinions. Platforms struggle to effectively facilitate conversations, leading many communities to limit or completely shut down user comments. What we are trying to accomplish here is to create an automated tool keep such uncouth activities in control.

## General links:
- Kaggle Competition: [Link][1]
- ConversationAI: [Link][2]


## Approaches explored:
- NBSVM (Baseline) : [Link][5]
- XGBoost: [Link][3]
- LightGBM: [Link][4]
- CNN: [Link][6]
- LSTM: [Link][7]
- Bi-Directional LSTM: [Link][8]

## Common Model Parameters:
- Vocabulary size = 6500
- Maximum sentence size = 400
- Embedding Size = 50
- Make only one model for multi-class classification and not 6 separate models for 6 separate classes

[1]: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge
[2]: https://conversationai.github.io/
[3]: ../XGBOOST/README.md
[4]: ../light-gbm/README.md
[5]: ../baseline/NBSVM.ipynb
[6]: ../djksf
[7]: ../sajfud
[8]: ../sajkhjfd