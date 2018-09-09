
_Input:_

```python
%pyspark
import matplotlib
import pandas as pd


df = pd.read_csv('https://ed-public-download.app.cloud.gov/downloads/Most-Recent-Cohorts-All-Data-Elements.csv', usecols=['INSTNM', 'ADM_RATE', 'SAT_AVG'] )

 
```


---


_Input:_

```python
%pyspark
df.dropna()
```


---


_Input:_

```python
%pyspark
elite=df.loc[(df['ADM_RATE'] < 0.07) & (df['ADM_RATE'] > 0) & (df['SAT_AVG'] > 0)]
elite.head(10)

excellent=df.loc[(df['ADM_RATE'] < 0.09) & (df['ADM_RATE'] > 0.9) & (df['SAT_AVG'] > 0)]
```


---


_Input:_

```python
%pyspark
elite['ADM_RATE'].plot.hist()
```


---


_Input:_

```python
%pyspark
z.show(elite)

 
```


---


_Input:_

```python
%pyspark
elite.plot.scatter(x='SAT_AVG', y='ADM_RATE')
```


---


_Input:_

```python
%pyspark
elite.plot.hexbin(x='SAT_AVG', y='ADM_RATE',gridsize=25)
```


---


_Input:_

```python
%pyspark
excellent.plot.hexbin(x='SAT_AVG', y='ADM_RATE',gridsize=25)
```


---


_Input:_

```python
%pyspark
excellent=df.loc[(df['ADM_RATE'] < 0.4) & (df['ADM_RATE'] > 0.09) & (df['SAT_AVG'] > 0)]
print(excellent.shape)

z.show(excellent)
```


---


_Input:_

```python
%pyspark
excellent.plot.scatter(x='SAT_AVG', y='ADM_RATE')
```


---


_Input:_

```python
%pyspark
elite.plot.bar(stacked=True)
print(elite.shape)
```


---


_Input:_

```python
%pyspark
elite.plot.area()
```


---


_Input:_

```python
%pyspark
costs = pd.read_csv('https://ed-public-download.app.cloud.gov/downloads/Most-Recent-Cohorts-All-Data-Elements.csv', usecols=['INSTNM','COSTT4_A'] )
```


---


_Input:_

```python
%pyspark
z.show(costs)
```


---


_Input:_

```python
%pyspark
def expense(tuition):
    return int(tuition/5000)
```


---


_Input:_

```python
%pyspark
expense(20000)
```


---


_Input:_

```python
%pyspark
tuition = costs['COSTT4_A']
```


---


_Input:_

```python
%pyspark
x= tuition.dropna()
```


---


_Input:_

```python
%pyspark
costRange = x.apply(expense)
```


---


_Input:_

```python
%pyspark
x
```


---


_Input:_

```python
%pyspark
x
```


---


_Input:_

```python
%pyspark
costRange.value_counts().plot.bar()
```
