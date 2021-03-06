# Useful methods examples and description.


## Dataframe


#### Describe

``` python
df.describe()

# Additional fields observation
df.describe(include=['object', 'bool'])

```

The describe method shows basic statistical characteristics of each numerical
feature (int64 and float64 types): number of non-missing
values, mean, standard deviation, range, median, 0.25 and 0.75 quartiles.


#### Value counts

For categorical (type object) and boolean (type bool) features we can use the value_counts method.

``` python
df['Col'].value_counts()

# Sample:
# 0    2850
# 1     483
# Name: Churn, dtype: int64
```

To calculate fractions, pass ```.value_counts(normalize=True)```.

#### Map


The map method can be used to replace values in a column by passing a dictionary of the form {old_value: new_value} as its argument.

``` python
d = {'No' : False, 'Yes' : True}
df['International plan'] = df['International plan'].map(d)
df.head()
```

#### Summary tables

``` python
# Cross tables
pd.crosstab("Col1", "Col2")

# Pivot tables
df.pivot_table(['Total day calls', 'Total eve calls', 'Total night calls'],
               ['Area code'], aggfunc='mean')
```
This will resemble **pivot tables** to those familiar with Excel. And, of course, pivot tables are implemented in Pandas: the pivot_table method takes the following parameters:

- values – a list of variables to calculate statistics for,
- index – a list of variables to group data by,
- aggfunc – what statistics we need to calculate for groups, ex. sum, mean, maximum, minimum or something else.


--------------------------------------------

# Refference

## Style guide

1. Command name 2rd order header.
1. Link to documentation.
2. Method signature.
3. Main parameters description.
4. Description with at least 1 example.


## PandasMethod

``` python
method
```
- param1 - description
> Method description

``` python
example
```
-------------------------------------

## pandas.melt

``` python
pandas.melt(frame,
            id_vars=None,
            value_vars=None,
            var_name=None,
            value_name='value',
            col_level=None,
            ignore_index=True
            )
```
- id_vars ```tuple, list, or ndarray, optional```

Column(s) to use as identifier variables.
- value_vars ```tuple, list, or ndarray, optional```

Column(s) to unpivot. If not specified, uses all columns that are not set as id_vars.

-var_name ```scalar```
Name to use for the ‘variable’ column. If None it uses frame.columns.name or ‘variable’.
value_namescalar, default ‘value’

Name to use for the ‘value’ column.
col_levelint or str, optional

If columns are a MultiIndex then use this level to melt.
ignore_indexbool, default True

If True, original index is ignored. If False, the original index is retained. Index labels will be repeated as necessary.

``` python
example
```
