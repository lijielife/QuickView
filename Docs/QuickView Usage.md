# __QuickView__

### Installing QuickView
QuickView has been published to PyPI [here](https://pypi.python.org/pypi/QuickView/0.1). You can install it with `pip install quickview` or download the tar.gz file from PyPI, extract it and run `python setup.py install` in the extracted directory. 

If you want to try the latest version you can clone this repository, extract and run `python setup.py install` in the extracted directory. Note that, this repo _may_ contain an in-progress version which is yet to be updated at PyPI. I'll keep pushing incrementally to the repo whenever I complete a feature/smallest working incremental unit. I will publish an update to the PyPI if I think the updates are significant. Features not yet updated/published in PyPI are marked with asterisk.

### Using QuickView
To use QuickView, you just need to import the package and call visualize method passing the pandas dataframe. The method outputs useful summaries about the dataset, plots number of null values colum-wise, number of unique values in categorical columns and correlation matrix of all attributes.

```python
import QuickView.DataFrameVisualizer as qv
import pandas as pd

# Just call the visualize method and pass the pandas dataframe
qv.visualize(pd.read_csv('data.csv'))
```

### QuickView.DataFrameVisualizer.visualize() Parameters
|Parameter Name | Required | Description|
|:--------------|:---------|:-----------|
|df | Yes | Pandas Dataframe object |
| print_summaries | No, Default: True | Indicates whether the summaries are to printed or not |
| cat_pthreshold | No, Default: 5 | Percentage of Unique values in a text column above which, a column is to be considered as categorical |
| cat_cthreshold | No, Default: -1 | Count of Unique values in a text column above which, a column is to be considered as categorical |

If both _cat_pthreshold_ and _cat_cthreshold_ are provided, a column is considered as categorical if the unique values meet one of the threshold criteria. To ignore one of those, set the value to -1. By default, if unique values less than 5% of the total number of records, the column is considered categorical.

### QuickView.DataFrameVisualizer Properties
These properties reflect values only after calling `QuickView.DataFrameVisualizer.visualize()` method.

|Parameter Name | Description|
|:--------------|:-----------|
|row_count | Number of rows in the dataframe |
|column_count | Number of columns in the dataframe |
|numeric_column_names | List of numeric column names |
|text_column_names | List of text column names |
|categorical_column_names | List of categorical column names |
|categorical_column_values | Dict of Column names and distinct categrical values |
|categorical_column_values_counts | Dict of Column names and number of distinct categrical values |
|rows_with_nulls | Pandas dataframe object containing rows with at least one null/na values |
|columnwise_null_values_count | Dict of Column names and number of null/na values |
|min_max_mean_std | Pandas dataframe object containing min, max, mean and standard deviation of all numeric columns |
|loaded | Boolean, Indicates whether all the values have been updated |


#### Dataset Attribution
Dataset used in the QuickView Example.ipynb notebook was provided by HackerEarth for the [Machine Learning Challenge](https://www.hackerearth.com/challenge/competitive/machine-learning-challenge-one/machine-learning/bank-fears-loanliness/) I participated earlier. You can download the dataset from the challenge page link or try out with your own dataset.
