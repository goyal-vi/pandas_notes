1. Automatic and explicit data alignment: objects can be explicitly aligned to a set of labels, or the user can simply ignore the labels and let Series, DataFrame, etc. automatically align the data for you in computations
2. Hierarchical labeling of axes (possible to have multiple labels per tick)
3 .Time series-specific functionality: date range generation and frequency conversion, moving window statistics, moving window linear regressions, date shifting and lagging, etc.
4. All pandas data structures are value-mutable (the values they contain can be altered) but not always size-mutable. 
5. The length of a Series cannot be changed, but, for example, columns can be inserted into a DataFrame. 
6. However, the vast majority of methods produce new objects and leave the input data untouched. 
7. In general we like to favor immutability where sensible.
8. dates = pd.date_range('20130101', periods=6)
9. __DataFrame.to_numpy() gives a NumPy representation of the underlying data. Note that his can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. When you call DataFrame.to_numpy(), pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame. This may end up being object, which requires casting every value to a Python object.__
10. [here][1] For df, our DataFrame of all floating-point values, DataFrame.to_numpy() is fast and doesn’t require copying data.
11. Note DataFrame.to_numpy() does not include the index or column labels in the output.
12. While standard Python / Numpy expressions for selecting and setting are intuitive and come in handy for interactive work, for production code, we recommend the optimized pandas data access methods, **.at, .iat, .loc and .iloc.**

#### Accessing data from pandas dataframe
1. Selecting a single column, which yields a Series, equivalent to df.A:
 df['A']
2. Selecting via [], which slices the rows.
 df[0:3] 
3. For getting a scalar value:
 df.loc[dates[0], 'A']
4. For getting fast access to a scalar (equivalent to the prior method):
 df.at[dates[0], 'A'] 
5. For getting a value explicitly:
df.iloc[1, 1]
0.17321464905330858
For getting fast access to a scalar (equivalent to the prior method):
df.iat[1, 1]
-0.17321464905330858 
6. df2[df2['E'].isin(['two', 'four'])]
7. To drop any rows that have missing data.
  df1.dropna(how='any')
8. To get the boolean mask where values are nan.
  pd.isna(df1)
9. Operations in general exclude missing data.
   Performing a descriptive statistic: 
   df.mean(axis_number) axis_number = 0 by default
10. Series is equipped with a set of string processing methods in the str attribute that make it easy to operate on each element of the array, as in the code snippet below. Note that pattern-matching in str generally uses regular expressions by default (and in some cases always uses them). See more at Vectorized String Methods.
  s.str.lower()
11. By “group by” we are referring to a process involving one or more of the following steps:
  Splitting the data into groups based on some criteria
  Applying a function to each group independently
  Combining the results into a data structure
  
   
[1]: https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html
