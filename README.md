# ml-homework
Used One hot encoding for columns with unique variable count smaller than five and used OrdinalEncoding on the rest.
Used linear regression for training.
Experiment #1(Linear regression):
    Run #1:
    Delt with Na in the following way:
        for columns with a lot of Na-s I just delete them.
        for others I just filled them with the most frequent value 
    Used One hot encoding for columns with unique variable count smaller than five and used OrdinalEncoding on the rest.
    Used linear regression for training.

    got Mean squared error on train: 28511.80919690585 and Mean squared error on test: 33228.35741244413
    the r2 score on train: 0.863707536709239 and on test: 0.8560525711025742

    Run #2:
    used a standard scaler. Yielded similar but a bit worse results:
        Root Mean Squared Error (Train): 28702.64012077323
        Root Mean Squared Error (Test): 33029.116941351116
        R2 Score (Train): 0.8618770070755408
        R2 Score (Test): 0.8577736413735249

    Run #3:
    used a MinMax scaler. Yielded similar but a bit worse results:
        Root Mean Squared Error (Train): 28702.64012077323
        Root Mean Squared Error (Test): 33029.116941351116
        R2 Score (Train): 0.8618770070755408
        R2 Score (Test): 0.8577736413735249

Experiment #2(Decision Tree):
    Run#1:
        ran it without an scaler and delt with na like we did in the last experiment.
        This yielded the following results:
            Root Mean Squared Error (Train): 0.0
            Root Mean Squared Error (Test): 42947.989718490775
            R2 Score (Train): 1.0
            R2 Score (Test): 0.759523940568361
        Since rmse on train is 0 we can confidently say that we are overfitting and the results on test returned worse
        results compared to linear regression.
    
    Run #2:
        used a standard scaler. Yielded similar but a bit worse results:
            Root Mean Squared Error (Train): 0.0
            Root Mean Squared Error (Test): 42974.246598701735
            R2 Score (Train): 1.0
            R2 Score (Test): 0.7592298135905118
        this returned worse results than the first run and its still overfitting.
    
    Run #3:
        used a MinMaxScaler scaler. Yielded a bit better results:
            Root Mean Squared Error (Train): 0.0
            Root Mean Squared Error (Test): 40468.7717526043
            R2 Score (Train): 1.0
            R2 Score (Test): 0.7864860707449662
        this returned better results than the first run and its still overfitting.