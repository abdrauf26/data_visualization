# Data Visualization Using Python

## 1. Correlation Matrix 
```
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, FormatStrFormatter

import seaborn as sns
sns.set()
```
```
sns.heatmap(df_singapore_condo_apt_data.corr(),cmap='YlGn',annot=True)

plt.title('Singapore Condominiums and Apartments correlation matrix')
```

![image](https://user-images.githubusercontent.com/96287600/178271201-cff3f6e9-3ec8-4918-b215-2dd8c66244c0.png), <p align="center">


