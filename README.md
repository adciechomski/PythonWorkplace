import pandas as pd
import numpy as np
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
df = (df[["close_price", "volume"]]).astype(float)
new_df = df.head(10)
indexParam = new_df.reset_index(level=0)["begins_at"]

print(pd.DataFrame(np.random.randn(10,4), index=indexParam, columns=('one','two','three','four')))
print(new_df.join(pd.DataFrame(np.random.randn(10,4), index=indexParam, columns=('one','two','three','four'))))
print(new_df.join(pd.DataFrame(np.random.randn(10,4), index=indexParam, columns=('one','two','three','four'))).dtypes)
sample = new_df.join(pd.DataFrame(np.random.randn(10,2), index=indexParam, columns=('one','two')))#.describe()
np.set_printoptions(threshold=np.nan)
pd.set_option('display.max_rows', len(sample))
print(sample)

#df.to_csv('quotasList1.csv', columns = ["close_price", "volume"])
#new_df.plot()
#plt.show()
