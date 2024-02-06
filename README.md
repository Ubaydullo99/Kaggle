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


underfitting and overfitting

![image](https://github.com/UbaydullohML/ML-Kaggle/assets/75980506/34af354e-dff2-4015-a10e-c4f6f2a33d6f)

![image](https://github.com/UbaydullohML/ML-Kaggle/assets/75980506/ce7af62e-ef2d-49ea-a79b-81b42878d760)

    # max_leaf_nodes - sensible way to control overfitting and underfitting
    from sklearn.metrics import mean_absolute_error
    from sklearn.tree import DecisionTreeRegressor
    def get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y):
        model = DecisionTreeRegressor(max_leaf_nodes=max_leaf_nodes, random_state=0)
        model.fit(train_X, train_Y)
        pred_val = model.predict(val_X)
        mae=mean_absolute_error(val_y, pred_val)
        return(mae)

    # compare MAE with different values of max_leaf_nodes
    for max_leaf_nodes in [5,50,500,5000]:
        my_mae = get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y)
        print('Max leaf nodes: &d \t\t Mean absolute error: %d' %(max_leaf_nodes, my_mae)

![image](https://github.com/UbaydullohML/ML-Kaggle/assets/75980506/b78342a9-837a-44ae-8952-a4e9d68045a2)

    
    
