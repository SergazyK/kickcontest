# kickcontest

Solutions to Machine Learning contest #2 Hackerearth.com
2nd place on public LB and same on private LB

Solution overview:

<h2>Important features added:</h2>
Bag of words technique was used. It was strange, but removing stopwords gave slightly worse results. CountVectorizer was the best one from all available on sklearn. I thought about trying out sent2vec averaged from word2vec or Glove vectors but didn't have time to do so.

Readability score of the text description. There are nice packages out there in github for computing readability score they include FleschKincaidGradeLevel, Automated Readability Index etc.

I've counted number of valid english words in the description with enchant library. Also used nltk.Vader to computer sentiment scores for desciption and name of the campaign. The compoundScore especially was always in the top of feature importances
There were computed many text features like number of digits, commans, len, count etc.

For some reason kkstid was also in top 5 of feature importances. Inspecting ID of project I thought that it is somehow related to time or category, I decided to leave it anyway.

Here are mysterious features: hardness and potentiality. Their formulas are money/duration, money\*duration respectively. At first glance hardness should be more important than potentiality, but guess what? It is not alway true. Potentiality was top 1 feature in my model:)

I've also tried to cluster description by k-means clustering based on tf-idf vectors, but it gave me no gain.

<h2>Model:</h2>
I've found out-of-box LightGBM better than XGBoost both in performance and accuracy. I've also tried RandomForest but it gave 2-3% decrease in acc, others I've tried are SVM, LinearSVM, Logistic Regression, Vowpal Wabbit's logistic regression(max_features = inf), AdaBoost, ExtraTrees, kNN, LSTM, RNN, FNNs etc. None of them stood nearby Gradient Boosting Machine. Since I'm newcomer to ML competitions I didn't know how to properly stack/ensemble models and didn't save models that gave poor results, sooner I apologized on my mistake but didn't want to rerun those complex models and decided to keep only one LSTM and LightGBM.

This report was written for Hackerearth contestants
