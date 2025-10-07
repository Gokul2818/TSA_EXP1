# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 07-10-2025

# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.
# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.
# PROGRAM:

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv("/content/jee_mains_2013_to_2025_top_30_ranks.csv")
data
data['Year'] = pd.to_datetime(data['Year'], format='%Y')
data.set_index('Year', inplace=True)

numeric_cols = data.select_dtypes(include=[np.number]).columns
data['AvgRank'] = data[numeric_cols].mean(axis=1)

result = seasonal_decompose(data_aggregated['AvgRank'], model='additive', period=1)
data_aggregated['rank_resid'] = result.resid


data_aggregated['rank_log'] = np.log(data_aggregated['AvgRank'])
data_aggregated['rank_log_diff'] = data_aggregated['rank_log'] - data_aggregated['rank_log'].shift(1)


result_log = seasonal_decompose(data_aggregated['rank_log_diff'].dropna(), model='additive', period=1)
data_aggregated['rank_log_resid'] = result_log.resid

plt.figure(figsize=(10, 5))
plt.plot(data_aggregated['AvgRank'], marker='o', label='Average Rank (Top 30)')
plt.title('JEE Mains Top 30 Average Rank (2013–2025)')
plt.xlabel('Year')
plt.ylabel('Average Rank')
plt.legend()
plt.show()

plt.figure(figsize=(16, 14))

plt.subplot(5, 1, 1)
plt.plot(data_aggregated['rank_diff'], marker='o', label='Rank Difference')
plt.legend(loc='best')
plt.title('Rank Differencing')

plt.subplot(5, 1, 2)
plt.plot(data_aggregated['rank_resid'], marker='o', label='Residuals')
plt.legend(loc='best')
plt.title('Residuals from Decomposition')

plt.subplot(5, 1, 3)
plt.plot(data_aggregated['rank_log'], marker='o', label='Log Transform')
plt.legend(loc='best')
plt.title('Log Transformed Rank')

plt.subplot(5, 1, 4)
plt.plot(data_aggregated['rank_log_diff'], marker='o', label='Log Differencing')
plt.legend(loc='best')
plt.title('Log Differenced Rank')

plt.subplot(5, 1, 5)
plt.plot(data_aggregated['rank_log_resid'], marker='o', label='Log Residuals')
plt.legend(loc='best')
plt.title('Residuals (Log Differenced)')

plt.tight_layout()
plt.show()
```
# OUTPUT:
<img width="855" height="470" alt="image" src="https://github.com/user-attachments/assets/6197cf59-4815-4fb0-bb0c-2405d7809585" />

<img width="1303" height="251" alt="image" src="https://github.com/user-attachments/assets/fa806b52-05cd-4f93-a8a4-af404e64d624" />

<img width="567" height="129" alt="image" src="https://github.com/user-attachments/assets/40e1a9b8-0136-43da-8ecd-ec261c1cf111" />

<img width="565" height="129" alt="image" src="https://github.com/user-attachments/assets/a3cf6467-7df3-4d07-af02-307a95630d9f" />

<img width="630" height="121" alt="image" src="https://github.com/user-attachments/assets/71d5e50b-6dcc-4a36-bf9d-002211188acc" />

# RESULT:
Thus we have created the python code for plotting the time series of given data.
