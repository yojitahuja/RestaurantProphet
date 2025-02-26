# Restaurant Prophet

Restaurant Prophet is a predictive analytics tool designed to help restaurant chains and business owners determine the success potential of a restaurant in a given location before investing. By leveraging data science and machine learning, it analyzes multiple factors such as location attributes, restaurant type, and historical success trends to provide data-driven insights.

## Features
- Predicts the success rate of a restaurant based on given parameters.
- Uses machine learning models trained on real-world restaurant data.
- Analyzes geographical and business-specific features to determine profitability.
- Provides insights to aid restaurant expansion and decision-making.

## Dataset
This project uses a dataset containing:
- Latitude and longitude of existing restaurants.
- Type of restaurant (e.g., fast food, fine dining).
- Success metrics based on historical performance.

## Data Cleaning & Preprocessing
The dataset undergoes a thorough cleaning and preprocessing pipeline to ensure data quality and accuracy. Key steps include:

- **Removing Unnecessary Columns:** Non-essential attributes such as postal codes and external platform support are dropped.
- **Handling Missing and Invalid Data:** Entries with missing or invalid latitude and longitude values are removed to maintain geospatial accuracy.
- **Filtering by Geographic Boundaries:** Only restaurants within realistic boundaries of the Delhi NCR region are retained.
- **Standardizing Categorical Data:** City names, cuisines, and locality details are normalized for consistency.
- **Filling Missing Values:** Missing categorical values are replaced with placeholder labels to avoid data loss.
- **Removing Duplicates:** Duplicate entries are eliminated to prevent redundant influence on model training.
- **Processing Text Data:** Establishment types and locality names are cleaned and transformed into structured formats.
- **Encoding Categorical Features:** Establishment types and localities are mapped to numerical values for machine learning compatibility.
- **Handling Extreme Values:** Outliers such as zero latitude/longitude values are identified and removed.
- **Feature Scaling:** Numerical features like `average_cost_for_two` and `votes` are normalized using MinMax scaling to ensure uniform contribution to the model.
- **One-Hot Encoding for Categorical Data:** Highlights and cuisines are transformed using one-hot encoding, converting them into structured binary vectors for better representation in machine learning models.

This preprocessing ensures that the dataset is clean, structured, and ready for predictive modeling.

## Exploratory Data Analysis (EDA)
To better understand the dataset and extract meaningful insights, the following exploratory techniques are applied:

- **Geospatial Visualization with Folium:**
  - A map centered around Delhi NCR is generated to visualize restaurant locations using markers.
  - A heatmap is created to identify high-density areas of restaurant presence.
- **Correlation Analysis:**
  - A correlation matrix is computed to analyze relationships between key variables such as `aggregate_rating`, `average_cost_for_two`, `votes`, `establishment_mapped`, and `market_cluster`.
  - A heatmap is generated to visualize these correlations, helping in understanding the impact of different features on restaurant success.

These visualizations help in understanding spatial distributions and identifying key restaurant clusters within the region.

## Data Engineering
Advanced data engineering techniques are applied to enhance the dataset and extract additional features:

- **Locality-Based Aggregation:**
  - The dataset is grouped by `locality` to compute the average rating and votes for each locality.
  - These aggregated values are merged back into the dataset to provide locality-level insights.
- **Competition Density Calculation using BallTree:**
  - The dataset's latitude and longitude coordinates are converted into radians.
  - A BallTree with Haversine distance is built to efficiently calculate competition density.
  - Each restaurant's competition density is computed by counting nearby restaurants within a defined radius (2 km).

These engineered features help improve the predictive power of the model by incorporating localized competition and market trends.

## Models Used
Multiple machine learning models were tested to determine the best predictive performance:
- **XGBoost**
- **Random Forest Regressor**
- **Gradient Boosting**

## Technologies Used
- Python
- Pandas, NumPy, Scikit-learn
- Machine Learning (XGBoost, Random Forest Regressor, Gradient Boosting)
- Data Visualization (Matplotlib, Seaborn, Folium)
- Folium for geospatial analysis
- BallTree for spatial computations



