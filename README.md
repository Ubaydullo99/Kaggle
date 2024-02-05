# Kaggle

## Table of contents:

* [Data_Explore](#data_explore) 

## Data_explore 

    import pandas as pd
    file_path = '../input/melbourne-housing-snapshot/melb_data.csv'
    melbdata = pd.read_csv(file_path)
    melbdata.describe()   # summary of data


 

1st ml model

    import pandas as pd
    melbdata.columns      # listing all columns code

    melbdatana = melbdata.dropna(axis=0)     # drop not available = missing values

    y = melbdatana.Price     # dot notation = prediction target

    melbdata_features = ['Rooms', 'Bathroom', 'Lattitude', 'Longtitude', 'Landsize']     # choosing features
    X = melbdatana[melbdata_features]
    X.describe()
    X.head()
    
    from sklearn.tree import DecisionTreeRegressor
    #   define model, specify a number for random state to ensure same results each run
    melbmodel = DecisionTreeRegressor(random_state=1)
    melbmodel.fit(X,y)

    print('Making predictions for the following 5 houses')
    print(X.heaad())
    print('The predictions are')
    print(mebmodel.predict(X.head()))


model validation   - measure quality of model

    # On average, our predictions are off by about X.

    from sklearn.model_selection import train_test_split
    train_X, val_X, train_y, val_y = train_test_split(X,y, random_state = 0)
    melbmodel = DecisionTreeRegressor()
    melbmodel.fit(train_X, train_y)
    val_predictions = melbmodel.predict(val_X)
    print(mean_absolute_error(val_y, val_predictions))
    
    
    
    
