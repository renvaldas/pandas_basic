# pandas_basic

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

random_state = 333

rows_count = 20
colunms = ['A', 'B', 'C']
index = pd.date_range('2018-01-01', periods = rows_count)
mu, sigma = 10, 3 # mean and standard deviation

np.random.seed(random_state)
df = pd.DataFrame(
    np.random.normal(mu, sigma, (rows_count, 3)), 
    index=index, 
    columns=colunms)
    
fig = plt.figure(figsize=(12,5))
ax = fig.add_subplot(111)

ax.set(title='Graph title', 
    ylabel='Y-Axis',
    xlabel='X-Axis')

ax.plot_date(df.index.tolist(), df['A'], linestyle='-')
ax.plot_date(df.index.tolist(), df['B'], linestyle='--')
ax.plot_date(df.index.tolist(), df['C'], linestyle='-')

legend = ax.legend(loc='upper right', shadow=True)

plt.show()    
