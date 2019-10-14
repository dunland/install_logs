# Packages Cheat Sheets
Collection of small applications I have used the packages for.

## Matplotlib

### bekannte Fehler:
Wenn matplotlib nach Ausführen des Skripts alle Figs schließt, versuche die Zeile `matplotlib.use('Qt5Agg')` erneut auszuführen.

### backend
`matplotlib.use('renderer')`  
--> `matplotlib.rcsetup.all_backends` for all possible Strings

`matplotlib.use('Qt5Agg') # error: cannot load any qt binding`  
**--> Ubuntu:** `pip install PyQt5`  
**--> Win 10:** download Qt5 from from qt.io; (install PyQt5?)

### Position und Größe des Fensters bestimmen
#### using Qt5:
`plt.get_current_fig_manager().window.setGeometry(x,y,w,h)  # defines position for figure. (x, y, w, h from upper left screen margin) Only works with QT backend`

#### subplots:
`fig.subplots_adjust(left=0.08, right=0.98, bottom=0.05, top=0.9, hspace=0.4, wspace=0.3)`

### Legende
Legende außerhalb von Plot: `plt.legend(loc='best', bbox_to_anchor=(1.45,1))`  

### Ticks
[Übersicht Tick-Formatter:](https://matplotlib.org/3.1.1/gallery/ticks_and_spines/tick-formatters.html)  

![Übersicht über Tick-Formatter](img/python/mpl/tickFormatters.png)
``` python
# FormatStr formatter
ax = fig.add_subplot(n, 1, 4)
setup(ax)
ax.xaxis.set_major_locator(ticker.MultipleLocator(1.00))
ax.xaxis.set_minor_locator(ticker.MultipleLocator(0.25))
ax.xaxis.set_major_formatter(ticker.FormatStrFormatter(">%d<"))
ax.text(0.0, 0.1, "FormatStrFormatter('>%d<')",
        fontsize=15, transform=ax.transAxes)
```
### boxplot
`ax.boxplot(dataArray)`  
https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.boxplot.html  
https://matplotlib.org/3.1.1/gallery/statistics/boxplot_demo.html  
https://en.wikipedia.org/wiki/Quartile  
![Boxplot Quartile](img/Boxplot_vs_PDF.svg)  

### Animation
https://brushingupscience.com/2016/06/21/matplotlib-animations-the-easy-way/  
https://matplotlib.org/3.1.1/api/animation_api.html  
simple plot animation with draw() instead of plotting repetitively  

``` python
# %%
import matplotlib
matplotlib.use('Qt5Agg')
import matplotlib.pyplot as plt
import random

ysample = random.sample(range(-50, 50), 100)

xdata = []
ydata = []

plt.show()

axes = plt.gca()
axes.set_xlim(0, 100)
axes.set_ylim(-50, +50)
line, = axes.plot(xdata, ydata, 'r-')

for i in range(100):
    xdata.append(i)
    ydata.append(ysample[i])
    line.set_xdata(xdata)
    line.set_ydata(ydata)
    plt.draw()
    plt.pause(0.1)

# add this if you don't want the window to disappear at the end
plt.show()
```

### Draw between subplots:
https://www.cilyan.org/blog/2016/01/23/matplotlib-draw-between-subplots/

## Pandas DataFrames:  
`df` for DataFrames

`df.info()` for shape of object types of the data  
`df.describe()` returns a summary of statistics for numerical colums in the DataFrame  
`pd.DataFrame.merge()` Merge DataFrame or named Series objects with a database-style join.  
`pd.DataFrame.drop()` Drop specified labels from rows or columns.  
 `df.sort_values(by="column_name", axis=0, ascending=True, inplace=False, kind='quicksort', na_position='last')` sort by the values along either axis

 ### Accessing:
 `df.column('row')`  
 `df.loc['row', 'col']`  
 `df.iloc[4,2]` # [row, col]  

 selecting only some columns:
 `df_new = df[['col1', 'col2']]`

 **quickly filtering rows and creating columns:**  
 `df[df['column'] >= 5]`  
 `df.reset_index`  
 new column with operation: `df['new_col'] = df['some col'] * df['col B']`

### Altering DataFrames:

changing rows and colums: `df = df.transpose()`  
[merging DataFrames](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html#brief-primer-on-merge-methods-relational-algebra):
``` python
table = pd.DataFrame(columns=['id', 'osm_id', 'lons', 'lats']) # table 1
table['osm_id'] = table['osm_id'].astype(int) # make sure the type is the same

table2 = gebaeudeliste_import = pd.read_csv('Gebaeudeliste_import.csv', delimiter=';')

table = table.merge(table2, on='osm_id', how='left')

```

#### Changing index title:
https://stackoverflow.com/questions/19851005/rename-pandas-dataframe-index


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

---
## Shapely
get points from polygon:
``` python
polygon = some_polygon
pol_list = list(polygon.exterior.coords)
pol_df = pd.DataFrame(pol_list, columns=['long', 'lat'])
```

---
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
