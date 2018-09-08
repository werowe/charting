# charting

import matplotlib
import pandas as pd

df = pd.read_csv('https://ed-public-download.app.cloud.gov/downloads/Most-Recent-Cohorts-All-Data-Elements.csv', usecols=['INSTNM', 'ADM_RATE', 'SAT_AVG'] )

df.dropna()

elite = df.mask(lambda x: x['ADM_RATE'] <  0.1)

