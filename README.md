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
df = web.DataReader('AAPL', 'robinhood')

#df = df.set_index('begins_at')

df.reset_index(level=0, inplace=True)
#df.reset_index(level=0, inplace=True)
df = (df[["close_price", "volume"]])
print(df)
#df.to_csv('quotasList1.csv', columns = ["close_price", "volume"])
df.plot()
plt.show()
