# Data Visualization Using Python

## 1. Correlation Matrix 
```
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, FormatStrFormatter

import seaborn as sns
sns.set()

sns.heatmap(df_singapore_condo_apt_data.corr(),cmap='YlGn',annot=True)
plt.title('Singapore Condominiums and Apartments correlation matrix')
```

![image](https://user-images.githubusercontent.com/96287600/178271201-cff3f6e9-3ec8-4918-b215-2dd8c66244c0.png)

## 2. Parallel Coordinates Plot
```
 import plotly.express as px
import pandas as pd
df_singapore_condo_apt_data

fig = px.parallel_coordinates(
    df_singapore_condo_apt_data,
    dimensions=[
        'Unit Price ($psf)', 'Price ($)','No. of Units', 'Postal District','Year', 
    ],
    color='Year',
    color_continuous_scale=px.colors.sequential.Emrld)
fig.show()
```
![image](https://user-images.githubusercontent.com/96287600/178274149-639bea3a-f233-48d3-9f59-d92dd7171963.png)

## 3. Histogram
```
sns.histplot(df_singapore_condo_apt_data['Unit Price ($psf)'],kde=False, bins=30)

```
![image](https://user-images.githubusercontent.com/96287600/178274455-0ddbc861-3585-4c38-8170-4d828e51f991.png)

## 4. Boxplot
```
sns.boxplot(x="Year", y="Unit Price ($psf)", data=df_singapore_condo_apt_data, palette="coolwarm")
```
![image](https://user-images.githubusercontent.com/96287600/178274672-96bd7bab-2b10-4e77-9d5e-0cb6705a3ef3.png)

## 5. Plotly

```
import plotly
import plotly.graph_objs as go#graph objects
import plotly.offline as offline
offline.init_notebook_mode(connected=True)

# Plotly to analyze the Unit Price ($psf) - 2017 to 2022 dataset
trace0_1_overall = go.Box(y = df_singapore_condo_apt_data['Unit Price ($psf)'], 
               name = 'Unit Price ($psf)',
               marker_color = 'lightseagreen')

data = [trace0_1_overall]

offline.iplot(data)

```
![image](https://user-images.githubusercontent.com/96287600/178274953-44e65e8f-a371-40de-9b02-4787ad005a79.png)

## 6. Pairplot

```
sns.pairplot(df_singapore_condo_apt_data, hue='Type', palette='coolwarm')
```
![image](https://user-images.githubusercontent.com/96287600/178275094-bdb44941-80f9-4718-9be2-fa775ff7fee3.png)


## 7. Bar Chart

```
#Resampling for a frequency of 3 months
grouper = df_singapore_condo_apt_data.groupby(pd.Grouper(key="Date of Sale",  freq="3M"))
med_gp = grouper.median() #median value
med_gp = med_gp.drop(med_gp.index[20]) #drop 2022 as our analysis is from 2017 to 2021 for median resampling
med_gp.reset_index()
med_gp.index = ['Q1-2017', ' Q2-2017', 'Q3-2017', 'Q4-2017',
                'Q1-2018', ' Q2-2018', 'Q3-2018', 'Q4-2018', 
                'Q1-2019', ' Q2-2019', 'Q3-2019', 'Q4-2019',
                'Q1-2020', ' Q2-2020', 'Q3-2020', 'Q4-2020',
                'Q1-2021', ' Q2-2021', 'Q3-2021', 'Q4-2021',]

# Plot Median Unit Price ($psf) bar graph
med_gp.plot(kind='bar', y = 'Unit Price ($psf)', color = "skyblue", ec="grey", figsize=(20,10), rot =30, title= "Median Unit Price ($psf) 2017 to 2022")
plt.xlabel('Year')
plt.ylabel('Unit Price ($psf)')
plt.show()
```
![image](https://user-images.githubusercontent.com/96287600/178277144-d3d1bdb3-5da1-4bce-8513-773759ddb5c1.png)
