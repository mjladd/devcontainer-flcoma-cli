

# KNNClassifier
Classification with K Nearest Neighbours











## KNNClassifier vs. MLPClassifier[](#knnclassifier-vs-mlpclassifier)
FluCoMa includes another object for classification, the


- 
- 
- 
[MLPClassifier](/reference/mlpclassifier), which also uses supervised learning for classification. The KNN object works quite differently from the MLP object, each having their strengths and weaknesses. The main differences to know are that:the flexibility of the MLP objects make them generally more capable of learning complex relationships between inputs and outputs,the MLP objects involve more parameters and will take much longer to`fit`(aka. train) than the KNN objects, andthe KNN objects will likely take longer to make predictions than the MLP objects, depending on the size of the dataset (although they’re still quite quick!).