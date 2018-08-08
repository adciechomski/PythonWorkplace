import pandas as pd
import matplotlib.pyplot as plt
from matplotlib import style
pd.core.common.is_list_like = pd.api.types.is_list_like
import pandas_datareader.data as web
from datetime import datetime
style.use('ggplot')
symbol = 'WIKI/AAPL'  # or 'AAPL.US'
start = '2018-08-01'
end = '2018-08-03'
df = web.DataReader('F', 'robinhood')
#df.loc['2015-01-02']
print(df['close_price'])
#df.to_csv('quotasList.csv')
df.plot()
plt.show()
