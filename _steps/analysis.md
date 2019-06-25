---

title: Data Analysis With Python
nav_previous: extending
nav_next: visualizing
layout: page
---

It's time to put everything we've learned together and start doing some data analysis with Python! 

## Our dataset

The [dataset](../assets/files/Rossi.csv) we'll be working with today is one that was published in Peter H. Rossi, Richard A. Berk and Kenneth J. Lenihan's 1980 book, *Money, Work, and Crime: Some Experimental Results* (https://doi.org/10.1016/C2013-0-11412-2). The dataset is made available in the R *carData* package, and is described as follows: 

> This data set is originally from Rossi et al. (1980), and is used as an example in Allison (1995). The data pertain to 432 convicts who were released from Maryland state prisons in the 1970s and who were followed up for one year after release. Half the released convicts were assigned at random to an experimental treatment in which they were given financial aid; half did not receive aid. 

The [documentation page](https://vincentarelbundock.github.io/Rdatasets/doc/carData/Rossi.html) describes the columns that are present in the dataset.

![Step](../assets/images/step.png) Let's start by downloading this dataset into our Python project directory.

## The Pandas Package

To do our data analysis we'll be using the wildly popular data analysis package, pandas. 

If you're familiar with the R programming language then you'll feel right at home with Pandas. Pandas draws a lot of inspiration from R, particularly the Data Frame.

Let's start creating our analysis in the analysis.py file. 

Before we can use the package, make sure you've installed in by running the following command in the PyCharm terminal tab:

`conda install pandas`

## Importing Data With Pandas

Start by importing the pandas library at the top of our file with an import statement: 

```
import pandas as pd
```

In order to import a dataset, pandas provides a set of functions to import data from a variety of formats:

* `read_csv`
* `read_excel`

Our data is in CSV format, so we'll import it using the `read_csv` function: 

```
data = pd.read_csv('Rossi.csv')
```

<div class="aside" markdown="1">

## Objects in Python
We've already seen that variables in Python can have a type like int, float, or string. But there's also a whole host of more complex types like the pandas data frame. Often called *objects*, these more complex variables can hold your data just like a regular variable, but they might also keep other data as well.

For example, the data frame keeps a record of the number of columns and rows in our dataset. 

```
print(data.shape)
```

`(432, 62)`

In the above code, `shape` refers to some extra data that's stored in our object. We call this data an *attribute*, though you might also hear people call this a *property* or *member*.

In addition to data, objects like this can come with their own functions. For example, the pandas data frame comes with a `head()` function, which will return the first few rows from the dataset.

```
print(data.head())
```

{% highlight none %}
   week  arrest  fin  age   race wexp  ... emp47 emp48  emp49  emp50 emp51 emp52
0    20       1   no   27  black   no  ...   NaN   NaN    NaN    NaN   NaN   NaN
1    17       1   no   18  black   no  ...   NaN   NaN    NaN    NaN   NaN   NaN
2    25       1   no   19  other  yes  ...   NaN   NaN    NaN    NaN   NaN   NaN
3    52       0  yes   23  black  yes  ...   yes   yes    yes    yes   yes   yes
4    52       0   no   19  other  yes  ...    no    no     no     no    no    no
[5 rows x 62 columns]
{% endhighlight %}

In all these instances, we use the same dotted notation for the attributes of variables that we use for the functions in libraries because they have the same part-and-whole relationship.

</div>

## Exploring Our Data
To make sure our data has been imported correctly, we can use the data frame `info()` function:

```
print(data.info())
```

This gives us:

{% highlight none %}
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 432 entries, 0 to 431
Data columns (total 62 columns):
week      432 non-null int64
arrest    432 non-null int64
fin       432 non-null object
age       432 non-null int64
race      432 non-null object
wexp      432 non-null object
mar       432 non-null object
paro      432 non-null object
prio      432 non-null int64
educ      432 non-null int64
emp1      432 non-null object
emp2      431 non-null object
emp3      430 non-null object
emp4      429 non-null object
emp5      428 non-null object
emp6      427 non-null object
emp7      426 non-null object
emp8      425 non-null object
emp9      420 non-null object
emp10     418 non-null object
emp11     417 non-null object
emp12     415 non-null object
emp13     413 non-null object
emp14     412 non-null object
emp15     409 non-null object
emp16     407 non-null object
emp17     405 non-null object
emp18     402 non-null object
emp19     399 non-null object
emp20     397 non-null object
emp21     392 non-null object
emp22     390 non-null object
emp23     389 non-null object
emp24     388 non-null object
emp25     384 non-null object
emp26     381 non-null object
emp27     378 non-null object
emp28     376 non-null object
emp29     374 non-null object
emp30     374 non-null object
emp31     372 non-null object
emp32     371 non-null object
emp33     369 non-null object
emp34     367 non-null object
emp35     365 non-null object
emp36     361 non-null object
emp37     358 non-null object
emp38     354 non-null object
emp39     353 non-null object
emp40     351 non-null object
emp41     347 non-null object
emp42     347 non-null object
emp43     345 non-null object
emp44     341 non-null object
emp45     339 non-null object
emp46     337 non-null object
emp47     333 non-null object
emp48     332 non-null object
emp49     330 non-null object
emp50     325 non-null object
emp51     322 non-null object
emp52     322 non-null object
dtypes: int64(5), object(57)
memory usage: 209.3+ KB
{% endhighlight %}

Here we can see a variety of information about our data frame: 

* It has 432 entries and 63 columns of data
* For each column, we can see its name, the number of non-empty (non-null) values, and the data type that pandas has given to that column.
* The amount of memory that our data consumes

### Generating Summary Statistics

Another common way to get a feel for the data is to generate summary statistics for each column. If you have numeric columns, the `DataFrame.describe()` function generates the summary statistics of the columns that have numerical data. All other columns are ignored, unless you use the argument `include='all'`, in which case it will give some information like the number of unique values and the most common value.

```
print(data.describe())
```

Gives:

{% highlight none %}
             week      arrest         age        prio        educ
count  432.000000  432.000000  432.000000  432.000000  432.000000
mean    45.854167    0.263889   24.597222    2.983796    3.476852
std     12.662293    0.441251    6.113375    2.896068    0.833978
min      1.000000    0.000000   17.000000    0.000000    2.000000
25%     50.000000    0.000000   20.000000    1.000000    3.000000
50%     52.000000    0.000000   23.000000    2.000000    3.000000
75%     52.000000    1.000000   27.000000    4.000000    4.000000
max     52.000000    1.000000   44.000000   18.000000    6.000000
{% endhighlight %}

## Subsetting and Filtering Data with Pandas
Now that we've had a chance to explore our data a little bit, we can start to dig a little deeper.



### Selecting individual values

There are two ways to select individual values out of a data frame by numerical index or by name. To select data by numerical index we use the `iloc` property along with the square brackets to indicate which position we'd like to access:

```
top_left = data.iloc[0,0]
bottom_right = data.iloc[431, 61]
```

When selecting by index in Python we always start counting at the number 0, and count down and then out from the top left corner of our dataset.

So, in the following example, the code `data.iloc[0,0]` will produce the value `20`, while the code`data.iloc[4,4]` will produce the value `'other'`

{% highlight none %}
   week  arrest  fin  age   race wexp  ... emp47 emp48  emp49  emp50 emp51 emp52
0    20       1   no   27  black   no  ...   NaN   NaN    NaN    NaN   NaN   NaN
1    17       1   no   18  black   no  ...   NaN   NaN    NaN    NaN   NaN   NaN
2    25       1   no   19  other  yes  ...   NaN   NaN    NaN    NaN   NaN   NaN
3    52       0  yes   23  black  yes  ...   yes   yes    yes    yes   yes   yes
4    52       0   no   19  other  yes  ...    no    no     no     no    no    no
{% endhighlight %}

The other way to select individual values is by name. To select a value by name we use the `loc` property on the data frame object, and then use the same square bracket notation to indicate the names of the rows and columns we'd like to access:

```
top_left = data.loc[0,"week"]
bottom_right = data.loc[431, "emp52"]
```

By default the row index in this example is the same as the numerical index, but that's only because we haven't told pandas which column to use as the row index. If you have a column that you'd like to use for the row index, you can specify that as an argument when you read in your data:

```
data = pd.read_csv('Rossi.csv', index_col="index")
```

### Selecting Columns

We can use a similar notation to access entire columns of data from our dataset. This comes in handy when we want to run statistics on an individual column alone. For example, we can select the age column:

```
ages = data["age"]
print(ages)
```


# Filtering Rows by Value

Often it's useful to filter rows of your dataset by some condition. For example, our dataset includes a `fin` column that indicates whether the individual received financial support after their release. Let's filter our data to only include those individuals:

```
financial_support = data["fin"] == "yes"
data_financial_support = data[financial_support]
```

