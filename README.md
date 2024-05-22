# Matplotlib-for-Year-and-Data-points
This code will be used to display the data-points yearly

How to plot the data points and years using Matplotlib.pyplot and Matplotlib.dates 

import matplotlib.pyplot as plt
import numpy as np
import matplotlib.dates as dt
import pandas as pd

### Sample data and years passed##

years= pd.date_range (start='2000', periods= 24, freq='Y')
data_points= [1, 3, 2, 5, 7, 4, 6, 8, 9, 7, 5, 4, 6, 8, 9, 10, 7, 8, 5, 6, 2, 10, 8, 1]

### Print lengths of the arrays to debug#####

print(f"Length of years: {len(years)}")
print(f"Length of data_points: {len(data_points)}")

### Check if the length of years and data_points array matchs###

if len(years) != len(data_points):
    raise ValueError("The lengths of 'years' and 'data_points' must be same")

### Create a DataFrame for ease of handling###

df= pd.DataFrame({'Year': years, 'Data': data_points})

### Create a plot and just plot the data###

fig, ax= plt.subplots()
ax.plot(years, data_points, marker='o', linestyle='-')

## Set the YearLocator and DateFormatter####
ax.xaxis.set_major_locator(dt.YearLocator())
ax.xaxis.set_major_formatter(dt.DateFormatter('%Y'))

## Rotate and align the tick labels####
plt.setp(ax.get_xticklabels(), rotation=45, ha='right')

### Set the labels and Titles, also show the output
ax.set_xlabel('Year')
ax.set_ylabel('Data Points')
ax.set_title('Yearly Data Points')

plt.show()
