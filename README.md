## Objective
The objective of this assignment is to try and predict the stock prices using historical data from four companies IBM (IBM), Google (GOOGL), Amazon (AMZN), and Microsoft (MSFT).

We use four different companies because they belong to the same sector: Technology. Using data from all four companies may improve the performance of the model. This way, we can capture the broader market sentiment.

The problem statement for this assignment can be summarised as follows:

> Given the stock prices of Amazon, Google, IBM, and Microsoft for a set number of days, predict the stock price of these companies after that window.


## Business Value

Data related to stock markets lends itself well to modeling using RNNs due to its sequential nature. 
We can keep track of opening prices, closing prices, highest prices, and so on for a long period of time as these values are generated every working day. 
The patterns observed in this data can then be used to predict the future direction in which stock prices are expected to move. Analyzing this data can 
be interesting in itself, but it also has a financial incentive as accurate predictions can lead to massive profits.


### **Data Description**

You have been provided with four CSV files corresponding to four stocks: AMZN, GOOGL, IBM, and MSFT. The files contain historical data that were gathered from the websites of the stock markets where these companies are listed: NYSE and NASDAQ. The columns in all four files are identical. Let's take a look at them:

- `Date`: The values in this column specify the date on which the values were recorded. In all four files, the dates range from Jaunary 1, 2006 to January 1, 2018.

- `Open`: The values in this column specify the stock price on a given date when the stock market opens.

- `High`: The values in this column specify the highest stock price achieved by a stock on a given date.

- `Low`: The values in this column specify the lowest stock price achieved by a stock on a given date.

- `Close`: The values in this column specify the stock price on a given date when the stock market closes.

- `Volume`: The values in this column specify the total number of shares traded on a given date.

- `Name`: This column gives the official name of the stock as used in the stock market.

There are 3019 records in each data set. The file names are of the format `\<company_name>_stock_data.csv`.



## **Conclusion and Summary**

### **1. Data Insights**
- The dataset contains stock price data for four companies: **Amazon (AMZN)**, **Microsoft (MSFT)**, **Google (GOOGL)**, and **IBM**.
- Key features include **Open**, **High**, **Low**, **Close**, **Volume**, and **Stock_name**.
- The data spans from **2006 to 2017**, providing a comprehensive view of stock price trends over time.

### **2. Missing Values**
- Missing values were identified in columns **Open** and **Low** for specific rows.
- These were handled using the **Forward Fill method**, ensuring no data loss while maintaining the time series integrity.

### **3. Outliers**
- Outliers were observed in price-related features (**Open**, **High**, **Low**, **Close**).
- These outliers reflect natural variations in stock prices across companies rather than errors.
- The **IQR method** was used to remove extreme outliers, improving data quality for modeling.

### **4. Frequency Distribution**
- The histogram of stock volumes revealed a **right-skewed distribution**, indicating:
  - Most trades occur at lower volumes.
  - High-volume transactions are rare and likely represent institutional trades.

### **5. Correlation Analysis**
- Strong positive correlations were observed between **Open**, **High**, **Low**, and **Close** prices.
- Moderate negative correlation (~ -0.42) was found between **Volume** and price features, suggesting:
  - Higher prices are associated with lower trading volumes.

### **6. Time Series Analysis**
- Weekly, monthly, and quarterly trends were analyzed:
  - **Weekly patterns** showed short-term fluctuations.
  - **Monthly trends** revealed smoother cycles.
  - **Quarterly aggregates** highlighted longer-term seasonality.

### **7. RNN Models**
#### **Simple RNN**
- The Simple RNN model captured overall trends effectively but struggled with extreme fluctuations.
- Performance metrics:
  - **Mean Squared Error (MSE):** 2.4954
  - **Mean Absolute Error (MAE):** 0.9942
  - **R-squared (R²):** 0.9870

#### **LSTM Model**
- The LSTM model demonstrated improved performance, particularly in handling volatility.
- Performance metrics:
  - **Mean Squared Error (MSE):** 2.8036
  - **Mean Absolute Error (MAE):** 0.9225
  - **R-squared (R²):** High, indicating strong predictive accuracy.

### **8. Predictions**
- Predicted values closely followed actual trends but showed smoothing effects.
- Deviations were observed at peaks and troughs, indicating challenges in capturing extreme price movements.

### **9. Key Observations**
- **Amazon (AMZN):** High trading volume spikes around 2007–2009, followed by stabilization.
- **Microsoft (MSFT):** Stable high volumes until 2012, with gradual decline thereafter.
- **Google (GOOGL):** Sharp drop in volume post-2007, followed by consistent lower volumes.
- **IBM:** Moderate and consistent fluctuations across the entire period.

### **11. Final Summary**
- The analysis provided valuable insights into stock price trends, correlations, and trading behaviors.
- Both Simple RNN and LSTM models demonstrated strong performance, with LSTM showing better handling of volatility.
- The study highlights the importance of data preprocessing, feature engineering, and model selection in time series forecasting.


