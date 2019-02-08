Automatic and explicit data alignment: objects can be explicitly aligned to a set of labels, or the user can simply ignore the labels and let Series, DataFrame, etc. automatically align the data for you in computations
Hierarchical labeling of axes (possible to have multiple labels per tick)
Time series-specific functionality: date range generation and frequency conversion, moving window statistics, moving window linear regressions, date shifting and lagging, etc.
All pandas data structures are value-mutable (the values they contain can be altered) but not always size-mutable. 
The length of a Series cannot be changed, but, for example, columns can be inserted into a DataFrame. 
However, the vast majority of methods produce new objects and leave the input data untouched. 
In general we like to favor immutability where sensible.
dates = pd.date_range('20130101', periods=6)
### DataFrame.to_numpy() gives a NumPy representation of the underlying data. Note that his can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column. When you call DataFrame.to_numpy(), pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame. This may end up being object, which requires casting every value to a Python object.
[here][1] For df, our DataFrame of all floating-point values, DataFrame.to_numpy() is fast and doesn’t require copying data.

[1]: https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html