# AI-Powered Traffic Optimization

## Overview
This project aims to optimize urban traffic flow using the **Metro Interstate Traffic Volume** dataset. It employs a Random Forest Regressor to predict traffic volume based on temporal, weather, and synthetic signal timing features. The project also optimizes traffic signal timings for peak hours and provides visualizations to analyze traffic patterns and the impact of various factors like weather and holidays.

## Dataset
The dataset used is `Metro_Interstate_Traffic_Volume.csv`, which contains the following columns:
- **holiday**: Holiday name or "None" if not a holiday.
- **temp**: Temperature in Kelvin.
- **rain_1h**: Rainfall amount in mm in the past hour.
- **snow_1h**: Snowfall amount in mm in the past hour.
- **clouds_all**: Percentage of cloud cover.
- **weather_main**: Main weather condition (e.g., Clear, Rain).
- **weather_description**: Detailed weather description (e.g., light rain, sky is clear).
- **date_time**: Timestamp of the observation.
- **traffic_volume**: Number of vehicles per hour (target variable).

The dataset is preprocessed to handle missing values, encode categorical variables, extract temporal features (hour, day of week, month), and create interaction features for better model performance.

## Code Structure
The main code is provided in a Jupyter notebook: `Metro-Traffic-Optimization.ipynb`. The notebook is organized into the following sections:
1. **Imports and Setup**: Import required libraries (pandas, numpy, sklearn, matplotlib, seaborn) and set random seed for reproducibility.
2. **Data Loading and Preprocessing**:
   - Load the CSV file.
   - Handle missing values and convert `date_time` to datetime.
   - Extract temporal features (hour, day of week, month, is_weekend).
   - Encode categorical variables (`holiday`, `weather_main`, `weather_description`).
   - Add synthetic signal timing (30–120 seconds) and interaction features (e.g., temp × rain).
3. **Data Preparation**: Split data into training and testing sets (80/20 split).
4. **Model Training**:
   - Train a Random Forest Regressor with 100 trees and max depth of 15.
   - Evaluate using Mean Squared Error (MSE) and R² score.
5. **Feature Importance Visualization**: Plot a bar chart of feature importance scores.
6. **Traffic Volume Prediction**:
   - Predict traffic volume for a typical Monday under clear and rainy conditions.
   - Visualize predictions over a 24-hour period.
7. **Signal Timing Optimization**:
   - Optimize signal timing for 8 AM under clear and rainy conditions.
   - Visualize traffic volume vs. signal timing with optimal points highlighted.
8. **Traffic Pattern Visualizations**:
   - Plot average traffic volume by hour, day of week, holiday, and weather description.
9. **Weather Impact Visualization**:
   - Scatter plot of traffic volume vs. temperature, colored by rainfall and sized by cloud cover.

## Requirements
To run the notebook, you need the following Python packages:
- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib`
- `seaborn`

You can install them using pip:
```bash
pip install numpy pandas scikit-learn matplotlib seaborn
```

Additionally, ensure the `Metro_Interstate_Traffic_Volume.csv` file is in the same directory as the notebook.

## Usage
1. **Setup Environment**:
   - Install the required packages.
   - Place `Metro_Interstate_Traffic_Volume.csv` in the working directory.
2. **Run the Notebook**:
   - Open `Metro-Traffic-Optimization.ipynb` in Jupyter Notebook or JupyterLab.
   - Execute the cells sequentially to load data, train the model, and generate visualizations.
3. **Outputs**:
   - **Model Performance**: Printed MSE and R² scores.
   - **Visualizations** (saved as PNG files):
     - `feature_importance.png`: Feature importance bar chart.
     - `traffic_volume_prediction.png`: Predicted traffic volume for clear and rainy conditions.
     - `signal_timing_optimization.png`: Traffic volume vs. signal timing with optimal timings.
     - `traffic_patterns.png`: Traffic volume by hour, day, holiday, and weather description.
     - `weather_impact.png`: Scatter plot of traffic volume vs. temperature with weather effects.
   - **Optimized Signal Timings**: Printed optimal signal timings for 8 AM under clear and rainy conditions.

## Notes
- The `signal_timing` feature is synthetic, as it’s not present in the original dataset. It simulates traffic signal cycle lengths (30–120 seconds).
- The model assumes the CSV file is accessible. If the file is located elsewhere, update the file path in the `pd.read_csv` call.
- The notebook includes interaction features (e.g., temp × rain) to capture complex relationships, improving prediction accuracy.
- Visualizations are saved as PNG files in the working directory for easy reference.

## Future Improvements
- Incorporate real-time traffic data or additional datasets for more accurate predictions.
- Add geospatial features to model traffic at specific intersections.
- Implement dynamic signal timing optimization for multiple hours or days.

## License
This project is for educational purposes and uses the Metro Interstate Traffic Volume dataset, which is assumed to be publicly available. Ensure compliance with any dataset-specific licensing terms.