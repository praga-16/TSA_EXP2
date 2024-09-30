# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date: 30-092024
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION
```
PRAGATHEESVARAN A B
212221240039
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load your dataset
data = pd.read_excel('ECOMM DATA.xlsx')  # Adjust the file path as needed

# Convert 'Order Date' to datetime and group by date for mean values of 'Sales' (or any other relevant column like 'Profit')
data['Order Date'] = pd.to_datetime(data['Order Date'])
price = data.groupby('Order Date')['Sales'].mean().reset_index()  # Assuming 'Sales' is the column you're analyzing

# Linear trend estimation
x = np.arange(len(price))
y = price['Sales']  # Replace 'Sales' with 'Profit' if needed
linear_coeffs = np.polyfit(x, y, 1)
linear_trend = np.polyval(linear_coeffs, x)

# Plotting
plt.figure(figsize=(14, 7))
plt.plot(price['Order Date'], price['Sales'], label='Original Data', marker='o')  # Replace 'Sales' with 'Profit' if needed
plt.plot(price['Order Date'], linear_trend, label='Linear Trend', color='red')
plt.title('Linear Trend Estimation for Sales')
plt.xlabel('Date')
plt.ylabel('Sales')  # Replace 'Sales' with 'Profit' if needed
plt.legend()
plt.grid()
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
B- POLYNOMIAL TREND ESTIMATION
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the dataset
data = pd.read_excel('/mnt/data/ECOMM DATA.xlsx')  # Adjust the file path as needed

# Convert 'Order Date' to datetime and group by date for mean values of 'Sales'
data['Order Date'] = pd.to_datetime(data['Order Date'])
sales_data = data.groupby('Order Date')['Sales'].mean().reset_index()  # Assuming 'Sales' is the column you're analyzing

# Polynomial trend estimation (degree 2)
x = np.arange(len(sales_data))  # Create an index array for the x-axis
y = sales_data['Sales']  # Extract sales data for trend estimation
poly_coeffs = np.polyfit(x, y, 2)  # Fit a 2nd degree polynomial
poly_trend = np.polyval(poly_coeffs, x)  # Evaluate the polynomial at each x position

# Plotting
plt.figure(figsize=(14, 7))
plt.plot(sales_data['Order Date'], sales_data['Sales'], label='Original Data', marker='o', color='blue')  # Original sales data
plt.plot(sales_data['Order Date'], poly_trend, label='Polynomial Trend (Degree 2)', color='green')  # Polynomial trend line
plt.title('Polynomial Trend Estimation for Sales Data')
plt.xlabel('Order Date')
plt.ylabel('Sales (in currency)')  # Specify the currency if known
plt.legend()
plt.grid()
plt.xticks(rotation=45)  # Rotate x-axis labels for better visibility
plt.tight_layout()
plt.show()

```
### OUTPUT
A - LINEAR TREND ESTIMATION
![image](https://github.com/user-attachments/assets/87dadcc7-4dd6-4b13-b26b-61d17fcfa55e)

B- POLYNOMIAL TREND ESTIMATION
![image](https://github.com/user-attachments/assets/2d2d1bf9-4ea9-4be3-9a1a-32e75df1168b)

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
