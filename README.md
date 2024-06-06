# Apartment Rent Prediction

This project aims to predict apartment rental prices using various regression models. The data is preprocessed, visualized, and different machine learning models are applied to achieve the best prediction performance.

## Dataset

The dataset used for this project is `ApartmentRentPrediction.csv`. It contains various features such as amenities, location, number of bedrooms, bathrooms, etc., which are used to predict the apartment rental prices.

## Data Preprocessing

1. **Handling Missing Values**:
    - Columns like `amenities`, `pets_allowed`, `cityname`, and `state` had missing values, which were filled with appropriate values or the mode.
    - `address` was processed to extract road names, and missing values were forward-filled.

2. **Feature Engineering**:
    - Created a new column `price_category` to categorize prices into 'Low', 'Mid', and 'High'.
    - Added a column `in_area` to indicate if the location is within a specific area.
    - Created new columns `body_count` and `title_count` to represent the length of the description and title text.
    - Processed `amenities` to represent the number of top 15 frequent amenities.
    - Added `city_offer_what` column to categorize cities based on average rental prices.

3. **Encoding**:
    - Used Label Encoding for categorical columns like `category`, `source`, `currency`, `fee`, `price_type`, `address`, `cityname`, `state`, `pets_allowed`, `has_photo`, and `city_offer_what`.

4. **Normalization**:
    - Normalized the `price_display` column to remove outliers using Winsorization.

5. **Feature Selection**:
    - Dropped columns that were deemed unnecessary after encoding and transformation.

## Data Visualization

- Plotted the distribution of price categories across different categorical variables.
- Visualized the correlation matrix to understand the relationships between features.
- Created scatter plots and histograms to explore the distribution and relationships of numerical features.

## Model Training

### Models Used

1. **Linear Regression**
2. **Ridge Regression**
3. **Decision Tree Regressor**
4. **Random Forest Regressor**
5. **Polynomial Regression** (degree 2)

### Training Process

1. Split the dataset into training and testing sets.
2. Applied Polynomial Features for the polynomial regression model.
3. Trained each model on the training data.
4. Evaluated the models using Mean Squared Error (MSE) and R² score.

### Cross-Validation

- Performed 5-fold cross-validation on the Random Forest model to evaluate its performance.

## Model Evaluation

- Evaluated the performance of each model on the test set.
- Plotted the predicted vs actual prices for the Random Forest model.

## Results

- Mean Squared Error and R² score for each model were computed.
- Random Forest model achieved the best performance with the lowest MSE and highest R² score.

## Files

- `ApartmentRentPrediction.csv`: Dataset used for training and testing.
- `random_forest_reg_model.pkl`: Pickled Random Forest model.
- `label_encoders_reg.pickle`: Pickled label encoders for categorical variables.
- `city_offer_map.pkl`: Pickled dictionary mapping cities to their price categories.

## Visualization

- KDE plot for price distribution.
- Boxplot for price distribution.
- Bar plots and histograms for feature analysis.

## Usage

To use the trained Random Forest model for predictions:

1. Load the model:
    ```python
    import pickle
    with open('random_forest_reg_model.pkl', 'rb') as f:
        model = pickle.load(f)
    ```

2. Load the label encoders:
    ```python
    with open('label_encoders_reg.pickle', 'rb') as f:
        label_encoders = pickle.load(f)
    ```

3. Prepare the data as per the preprocessing steps mentioned above.

4. Use the model to make predictions:
    ```python
    predictions = model.predict(X_test)
    ```

## Conclusion

This project demonstrates the process of preprocessing data, feature engineering, training various regression models, and selecting the best model for predicting apartment rental prices.
