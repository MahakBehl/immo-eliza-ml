# Model card

## Project context

Immo Eliza ml is a machine learning model to predict prices of real estate properties in Belgium. After scraping, cleaning and analysing we have a dataset with around 75000 records and around 30 properties. This project is about trying and testing various different models to predict the price and select the best model. Train the model and display the predicted prices.

## Data

Input dataset = properties.csv in data folder

Target variable = price

Features =

    	Numerical Features : total_area_sqm,surface_land_sqm,nbr_frontages,nbr_bedrooms,terrace_sqm,garden_sqm,primary_energy_consumption_sqm,cadastral_income
    	flag/Indicator features : fl_furnished,fl_open_fire,fl_terrace,fl_garden,fl_swimming_pool,fl_floodzone,fl_double_glazing
    	categorical features : property_type,subproperty_type,region,province,locality,equipped_kitchen,state_building,epc,heating_type


## Model details

Models tested: 

1. LinearRegression
2. GradientBoostingRegressor
3. Lasso
4. RandomForestRegressor 

Final model chosen: **RandomForestRegressor**

Random Forest works is a type of machine learning model used for making predictions. Instead of relying on just one decision tree , it creates a whole "forest" of decision trees. Each decision tree is trained on a random subset of the data and makes its own prediction. Then, when you want to make a prediction with the Random Forest, it combines the predictions of all the individual decision trees to come up with a final prediction.

## Performance

Performance metrics for the models tested:

| |Train R² score|Test R² score|
|LinearRegression with only 3 features|0.071662744|0.07315962|
|LinearRegression with all features mentioned above|0.351409473|0.390939096|
|Lasso|0.351695782|0.391371062|
|GradientBoostingRegressor|0.646782201|0.619932342|
|RandomForestRegressor|0.795439313|0.631809884|
|RandomForestRegressor with Recursive Feature Elimination|0.646782201|0.619932342|
|RandomForestRegressor with GridSearchCV and Feature Scaling|0.95369031|0.639870213|


Also, tried GridSearchCV & Feature Scaling separately but have not stored the results.
Tried Random Forrest with different features combinations & multiple combinations of hyperparameters.

## Limitations

Random Forests can result in relatively large model sizes, making them huge to store and deploy, especially in memory-constrained environments.

## Usage

Dependencies : 
    sklearn
    Pandas
    joblib

To train the model:

    python train.py

To generate predictions:

    python predict.py -i "data/properties.csv" -o "output/predictions.csv"

Predicitions are generated in predictions.csv file output folder.

## Maintainers

For any issues or questions regarding the model, please contact mahakbehl@gmail.com