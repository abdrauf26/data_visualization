# Data Visualization Using Python

## # 1. Correlation Matrix

```
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, FormatStrFormatter

import seaborn as sns
sns.set()
```
...
# Create the correlation matrix using seaborn
sns.heatmap(df_singapore_condo_apt_data.corr(),cmap='YlGn',annot=True)

plt.title('Singapore Condominiums and Apartments correlation matrix')
...
![image](https://user-images.githubusercontent.com/96287600/178270529-76b4da58-5d6e-4b86-9a28-f90303eb4247.png)
