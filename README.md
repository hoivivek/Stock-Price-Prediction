# Stock Price Prediction

This project focuses on developing a Recurrent Neural Network (RNN) model to predict stock market prices based on historical data, specifically for Starbucks Corporation (SBUX) stock. The goal is to forecast future market trends to aid in investment analysis and decision-making.

## Project Overview
Stock market prediction is a challenging yet crucial task for investors and financial analysts. This project leverages the power of RNNs, which are well-suited for capturing patterns in sequential data like stock prices over time. By training an RNN model on historical stock data, we aim to accurately predict future stock price movements.

## Methodology

Data Collection: Historical stock data for Starbucks Corporation (SBUX) was collected from NASDAQ, covering the period from September 11, 2024, to March 10, 2025. The dataset included features such as Date, Close/Last, Volume, Open, High, and Low.

### Data Preprocessing:

The 'Close/Last' column was converted from string to numeric format by removing '$' symbols and commas.

The 'Date' column was converted to datetime objects and set as the index.

Only the 'Close/Last' column (representing the closing stock price of the day) was considered for analysis.

The data was normalized using MinMaxScaler from the Scikit-learn library, scaling values between -1 and 1 to improve training efficiency.

Sequential time series data was created with a timestep of 30 (to capture previous 30 days' prices) and a forecast length of 3 (to predict prices for the next 3 days).


### Model Development:

The dataset was split into training and testing sets with an 80:20 ratio.

The data was reshaped to [samples, timestep, features] to meet RNN input requirements.

Three distinct RNN models were built, each incorporating stacked 

SimpleRNN layers with ReLU activation functions and Dropout layers to prevent overfitting.

Each model's final layer was a Dense layer designed to output three predicted prices.

Models were compiled using Mean Squared Error (MSE) as the loss function and Adam as the optimizer.

### Model Training and Evaluation:

Each model was trained for 100 epochs with a batch size of 32.

Models were evaluated on the test data using 

Mean Squared Error (MSE) and Root Mean Squared Error (RMSE).

Predicted values were inverse-transformed to their original stock price levels.

### Prediction and Interpretation:

The trained models were used to predict the next three stock prices based on the most recent data sequence.

Future dates corresponding to the forecasted prices were generated for enhanced interpretability.

## Technologies Used

Keras/TensorFlow: For building and training the neural network models.

Scikit-learn: For data preprocessing, including data splitting and normalization (MinMaxScaler).

Pandas: For data handling and manipulation.

Matplotlib: For data visualization (e.g., plotting stock prices over time).


## Results

Three different RNN model architectures were tested, varying in complexity. The performance of each model was evaluated using MSE and RMSE:

### Model

| Model | MSE         | RMSE |
| :----------- | :-------------- | :----------- |
| Model 1 | 2.30  | 1.51         |
| Model 2 | 2.61   | 1.61         |
| Model 3 | 2.20  | 1.48         |


Based on the evaluation metrics, 

Model 3 demonstrated the best performance with the lowest MSE (2.20) and RMSE (1.48).

The predicted prices for March 11-13, 2025, from each model are as follows:


### Predicted Prices

| Date         | Predicted Price |
| :----------- | :-------------- |
| 2025-03-11   | $97.29         |
| 2025-03-12   | $98.03         |
| 2025-03-13   | $97.71         |


## Key Findings
Recurrent Neural Networks (RNNs) are effective in forecasting time-series data, such as stock prices, by learning temporal dependencies.


The models were able to predict future stock prices with reasonable accuracy by utilizing past sequences of data.

Performance tends to improve with deeper model architectures, as observed with Model 3 achieving the best results among the tested models.

