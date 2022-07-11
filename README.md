# Data Visualization Using Python

![image](https://user-images.githubusercontent.com/96287600/178280201-c66eaf20-b2dc-4088-a59a-8e7958f197c6.png)


## Built With 💻

- [![Jupyter Badge](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=fff&style=flat)](https://jupyter.org/try)
- [![Python Badge](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff&style=flat)](https://www.python.org/)
- Pandas
- Numpy
- Seaborn
- Matplotlib
- Plotly
- Chart Studio

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
![image](https://user-images.githubusercontent.com/96287600/178277516-7a9bc037-f16b-40de-b8a3-c945fd9c8966.png)

## [![Made withJupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)](https://jupyter.org/try)
- [Jupyter Notebook Document - Data Visualization Using Python](https://nbviewer.org/github/abdrauf26/data_visualization/blob/main/Data%20Visualization%20Using%20Python.ipynb)

## Social 📧 

[![Google Cloud Badge](https://img.shields.io/badge/Google%20Cloud-4285F4?logo=googlecloud&logoColor=fff&style=flat)](https://www.cloudskillsboost.google/public_profiles/c2ff4f8e-4f42-4380-b038-73104c7d98fc) [![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=fff&style=flat)](https://www.linkedin.com/in/abdrauf26/) [![Tableau Badge](https://img.shields.io/badge/Tableau-E97627?logo=tableau&logoColor=fff&style=flat)](https://public.tableau.com/app/profile/mohamed.abdul.rauf) [![GitHub Badge](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=fff&style=flat)](https://github.com/abdrauf26) [![Medium Badge](https://img.shields.io/badge/Medium-000?logo=medium&logoColor=fff&style=flat)](https://medium.com/@rauf.yusope) ![Profile views](https://gpvc.arturio.dev/abdrauf26) 

## Acknowledgements

- [Jupyter](https://jupyter.org/)
- [Conda](https://docs.conda.io/en/latest/)
- [Anaconda](https://anaconda.org/)
- [Pixabay](https://pixabay.com/)
- [URA - Private Residential Property Transactions](https://www.ura.gov.sg/realEstateIIWeb/transaction/search.action)
- [Github](https://github.com/)
- [Stack Overflow](https://stackoverflow.com/)
- [Jupyter nbviewer](https://nbviewer.org/)
- Badges - https://badges.pages.dev/
- Badges - https://naereen.github.io/badges/
- Badges - https://github.com/Ileriayo/markdown-badges#-office
