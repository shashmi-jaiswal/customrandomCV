# CustomrandomSearchCV
Create a custom RandomSearchCV using 
def RandomSearchCV(x_train,y_train,classifier, param_range, folds):
    # x_train: its numpy array of shape, (n,d)
    # y_train: its numpy array of shape, (n,) or (n,1)
    # classifier: its typically KNeighborsClassifier()
    # param_range: its a tuple like (a,b) a < b
    # folds: an integer, represents number of folds we need to devide the data and test our model
    
    1. Generate 10 unique values(uniform random distribution) in the given range "param_range" and store them as "params" 
     example: if param_range = (1, 50): we generate 10 random numbes in range(1,50)
    2. Divide numbers ranging from  0 to len(X_train) into groups= folds
        Exmaple:  If folds=3, and len(x_train)=100, we can devide numbers from 0 to 100 into 3 groups 
          group 1: 0-33, group 2:34-66, group 3: 67-100
          
    3.For each hyperparameter that we generated in step 1:
        # and using the above groups we have created in step 2 you will do cross-validation as follows
        # first we will keep group 1+group 2 i.e. 0-66 as train data and group 3: 67-100 as test data, and find train and
          test accuracies
        # second we will keep group 1+group 3 i.e. 0-33, 67-100 as train data and group 2: 34-66 as test data, and find
          train and test accuracies
        # third we will keep group 2+group 3 i.e. 34-100 as train data and group 1: 0-33 as test data, and find train and
          test accuracies
        # based on the 'folds' value we will do the same procedure
        
        # find the mean of train accuracies of above 3 steps and store in a list "train_scores"
        # find the mean of test accuracies of above 3 steps and store in a list "test_scores"
    4. return both "train_scores" and "test_scores"

    5. Call function RandomSearchCV(x_train,y_train,classifier, param_range, folds) and store the returned values into "train_score", and "cv_scores"
    6. Plot hyper-parameter vs accuracy plot as shown in reference notebook and choose the best hyperparameter
    7. Plot the decision boundaries for the model initialized with the best hyperparameter, as shown in the last cell of reference notebook
