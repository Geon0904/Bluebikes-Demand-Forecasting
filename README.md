Boston Bluebikes Hourly Demand Forecasting
DS 4420: Advanced Machine Learning | Northeastern University
Team: Geon Chang, Miles Mu, Peisong Yuan

Overview: 
Predicting hourly Boston Bluebikes demand using three machine learning methods: Autoregressive Modeling (AR), Bayesian Linear Regression, and Multi-Layer Perceptron (MLP).

Dataset & Preprocessing:
- Source: https://bluebikes.com/system-data
- Period: January–December 2025 (12 monthly ZIP files)
- Raw data: 4,614,300 trips
- Processed data: 4,614,267 rides aggregated into 8,760 hourly observations
- Preprocessing: Missing-value checks, duplicate detection, timestamp validation, and daylight-saving time (DST) handling

Models:
- AR(168): Manually implemented using NumPy least squares.
- Bayesian Ridge: Bayesian regression with calendar features and predictive uncertainty estimates.
- MLP (64, 32): Neural network using ReLU, Adam, L2 regularization, and early stopping.

Results: 
Data were split chronologically into training (January–August), validation (September–October), and testing (November 1–December 30). All models were evaluated on 1,271 common test hours.

The seasonal naive baseline achieved a test MAE of 127.58 and RMSE of 205.07. AR(168) achieved an MAE of 50.80 and RMSE of 76.72, while Bayesian Ridge achieved an MAE of 52.29 and RMSE of 81.72. MLP (64, 32) performed best, with the lowest test MAE of 43.43 and RMSE of 62.19.

However, AR used only historical demand, while MLP and Bayesian Ridge also included calendar features.
1. Download the 12 monthly ZIP files for 2025 from the [official Bluebikes dataset](https://bluebikes.com/system-data).
2. Place all ZIP files in one Google Drive folder without extracting them.
3. Open DS4420_Bluebikes_EDA.ipynb in Google Colab.
4. Select Runtime -> Run all, authorize Google Drive access, and enter the dataset folder path when prompted.
5. Verify the generated model results and figures.
   
Limitations & Future Work: 
Dependencies are listed in requirements.txt. Original trip-history files are not redistributed.
The study uses one year of data and one-step-ahead forecasting, excludes DST-affected periods, and does not include weather, holidays, special events, or station-level information. Future work includes comparing models using identical features and improving chronological validation.
