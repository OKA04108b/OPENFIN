# OPENSOURCE FINAL PROJECT
### Congifuration Instructions
 - I decided to divide the test size by 0.01. I put the test size differently to evaluate my code. I thought making the test size very small would result the train accuracy low, but I thought the test data would be more accurate than the train accuracy because the amount of trained data is large.
<pre>
<code>
X_train, X_test, y_train, y_test = sklearn.model_selection.train_test_split(X, y, test_size=0.01, random_state=0)
</code>
</pre>

 - I used a Cross Validation and for loop. I used for loop to decide the parameters. I used 8 ExtraTreesClassifiers and 1 KNeighborsClassifier. There are 4 ExtraTreesClassifiers which n_estimators is high and 4 ExtraTreesClassifiers which n_estimators is 1. From Cross Validation, I realized that ETC which has an n_estimator of 1 has great accuaracy at part of data that high estimators ETC incorrects. However, overall 1 estimator ETC accuracy was very low. So, I put same number of 1 estimator ETC and high estimator ETC. Then, I put KNeighborClassifier to increase accuracy. (For example, 4 low estimator ETC guess: no tumor, 4 high estimator ETC guess: meningioma_tumor, then KNC which has high accuracy classifier makes a decisive judgement)
<pre>
<code>
ETC1 = ExtraTreesClassifier(n_estimators = 76,max_depth = 64,max_features = 1,min_samples_split = 3,random_state = 1001, criterion='entropy')
ETC2 = ExtraTreesClassifier(n_estimators = 42,max_depth = 53,max_features = 1,min_samples_split = 3,random_state = 1012, criterion='entropy')
ETC3 = ExtraTreesClassifier(n_estimators = 25,max_depth = 40,max_features = 1,min_samples_split = 3,random_state = 2914, criterion='entropy')
ETC4 = ExtraTreesClassifier(n_estimators = 15,max_depth = 29,max_features = 1,min_samples_split = 3,random_state = 1785, criterion='entropy')
#Small n_estimators
ETC5 = ExtraTreesClassifier(n_estimators = 1,max_depth = 1,max_features = 1,min_samples_split = 3,random_state = 1051, criterion='entropy')
ETC6 = ExtraTreesClassifier(n_estimators = 1,max_depth = 1,max_features = 1,min_samples_split = 3,random_state = 5029, criterion='entropy')
ETC7 = ExtraTreesClassifier(n_estimators = 1,max_depth = 2,max_features = 1,min_samples_split = 3,random_state = 5708, criterion='entropy')
ETC8 = ExtraTreesClassifier(n_estimators = 1,max_depth = 3,max_features = 1,min_samples_split = 3,random_state = 5570, criterion='entropy')
#KNC
KNC1 = KNeighborsClassifier(n_neighbors=1)
   
models = [
    ('ETC1', ETC1),
    ('ETC2', ETC2),
    ('ETC3', ETC3),
    ('ETC4', ETC4),
    ('ETC5', ETC5),
    ('ETC6', ETC6),
    ('ETC7', ETC7),
    ('ETC8', ETC8),
    ('KNC1', KNC1),
]
</code>
</pre>

- Then, I used Hard VotingClassifier and Train it.
<pre>
<code>
#Hard Voting
VOTE  = VotingClassifier(models)
VOTE.fit(X_train, y_train)
y_pred = VOTE.predict(X_test)
</code>
</pre>

### Operating Instructions
 - Put your training dataset file path and load it
 - Then run the code from top to bottom
### Copyright and Licensing Information
 - MIT License
### Contact Information for the distributor and author
 - Name: Kyuan Oh 오규안
 - Email: oka04108@gmail.com
