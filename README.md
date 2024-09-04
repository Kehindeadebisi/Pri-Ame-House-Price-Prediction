# Choosing the Right Model: House Price Prediction Case Study

## Data Preprocessing

### Data Cleaning
The first step involved understanding the dataset by reviewing the rows, columns, data types, and descriptive statistics. Data cleaning was then performed, which involved checking for null values across columns. It was observed that all columns, except the price column, contained null values. Since approximately 10% of the data had nulls, removal was deemed inappropriate. Instead, modal imputation was applied to categorical columns, and median imputation was used for numerical columns.

### Exploration and Outliers
Exploratory data analysis was carried out, starting with a distribution check using a histogram. Outliers were identified through a boxplot, showing that the price column contained several outliers. These outliers were further examined and indexed, revealing 568 potential outliers. As these values appeared valid, capping based on the lower and upper bounds of the quartiles was implemented rather than removing the data points.

### Encoding and Feature Engineering
String columns were encoded using label encoding to avoid high dimensionality, given the large number of categories. A heatmap was used to evaluate multicollinearity between features, and all correlations were confirmed to be below 0.7, which is acceptable. The ID column, being irrelevant for model training, and the target column (price) were dropped.

## Model Training and Evaluation

### Model Selection
An initial split of the training data was performed to evaluate model performance. After the best models and hyperparameters were determined, the models were retrained using the entire dataset to take full advantage of the data.

Linear Regression, Decision Tree, Random Forest, and Gradient Boosting models were trained and used to provide baseline metrics for comparison. The following metrics were used to evaluate the models: Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared (R²).

The initial results for each model were as follows:

- **Linear Regression**
  - Mean Absolute Error: 550,389.89
  - Mean Squared Error: 546,300,489,406.9
  - R-squared (R²): 0.3575

- **Decision Tree**
  - Mean Absolute Error: 385,478.17
  - Mean Squared Error: 390,278,239,044.8
  - R-squared (R²): 0.5410

- **Random Forest**
  - Mean Absolute Error: 322,223.46
  - Mean Squared Error: 251,285,127,357.6
  - R-squared (R²): 0.7045

- **Gradient Boosting**
  - Mean Absolute Error: 312,294.42
  - Mean Squared Error: 212,917,508,816.4
  - R-squared (R²): 0.7496

Gradient Boosting performed the best with the lowest MAE and MSE values, along with the highest R² score.

### Hyperparameter Tuning
GridSearch was applied to optimize the model by evaluating a range of hyperparameters. Despite the computational expense, the dataset’s size made this feasible. The results after tuning showed further improvement:

- **Mean Absolute Error (MAE)**: 254,858.69
- **Mean Squared Error (MSE)**: 177,343,509,949.7
- **R-squared (R²)**: 0.7914

### Retraining
The best hyperparameters were then used to retrain the model with the entire training dataset, further improving the performance.

## Prediction
The test data was loaded and preprocessed. Price predictions for the test data were generated using the trained model, and a final DataFrame was created, linking the IDs with the predicted prices.
