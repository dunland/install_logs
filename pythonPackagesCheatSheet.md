# Packages Cheat Sheets
## Pandas DataFrames:  
`df` for DataFrames

`df.info()` for shape of object types of the data  
`df.describe()` returns a summary of statistics for numerical colums in the DataFrame  
`pd.DataFrame.merge()` Merge DataFrame or named Series objects with a database-style join.  
`pd.DataFrame.drop()` Drop specified labels from rows or columns.  
 `df.sort_values(by="column_name", axis=0, ascending=True, inplace=False, kind='quicksort', na_position='last')` sort by the values along either axis

 **quickly filtering rows and creating columns:**  
 `df[df['column'] >= 5]`
 `df.reset_index`
 new column with operation: `df['new_col'] = df['some col'] * df['col B']`

#### [pandas.Index](http://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Index.html):  
> class pandas.Index[source]  
>    Immutable ndarray implementing an ordered, sliceable set. The basic object storing axis labels for all pandas objects.

##### DataFrame für ein Jahr erzeugen:

``` python
# Create DataFrame for 2010
demand = pd.DataFrame(
    index=pd.date_range(pd.datetime(2010, 1, 1, 0),
                        periods=8760, freq='H'))
```
  `freq=H` for frequeny=hourly [s. pandas-docs](https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html#timeseries-offset-aliases)

##### mit weiteren Spalten füllen:  
``` python
demand['efh'] = bdew.HeatBuilding(
    demand.index, holidays=holidays, temperature=temperature,
    shlp_type='EFH',
    building_class=1, wind_class=1, annual_heat_demand=25000,
    name='EFH').get_bdew_profile()
```
## Numpy  
`np.array(python_list)` creates numpy-array from python list  
`np.shape` returns (rows, columns)  
`array_B = array_A < 5` returns an array of booleans..  
  `array_A[array_B]` will then return only the values where B = True  
`array[0,1]` row 0, col 1  
`array[:,5]` all rows, col 5 (complete column 5)  
`array[2:5, 3:10]` row 2-5, col 3-10  

![python lists vs numpy arrays](img\python\lists_vs_nparrays.png)

## Excel / csv:
`hour_factors = pd.read_csv(file, index_col=0)`