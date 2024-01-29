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
    
