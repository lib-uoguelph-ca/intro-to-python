---

title: Extending Python
nav_previous: functions
nav_next: analysis
layout: page
---

Looking at the list of built-in functions, you might wonder *"Is that it? Am I expected to build everything else from scratch?"*

Fortunately, the answer is no! Python uses a system known as modules to provide a wide array of extra functions and data types. In many other programming languages, we call these **libraries**. In the Python world, they're known more formally as **modules**, though we'll use the term library interchangeably.

The Python documentation provides a nice index of all of the modules available as part of the [Python Standard Library](https://docs.python.org/3/library/index.html#library-index). Some examples:

* The [math](https://docs.python.org/3/library/math.html) module includes functions to help us do advanced math like finding the greatest common divisor between two numbers, summing a list of numbers, or converting angles from degrees to radians. 
* The [re](https://docs.python.org/3/library/re.html) module provides tools for pattern matching in text data.
* The [datetime](https://docs.python.org/3/library/datetime.html) module adds new date types and functions for manipulating dates. 

## Enabling a Module

Before we can use a module we have to first make it available for use in our code using an **import** statement. Technically these can go anywhere in your code though it's good practice to include all of your module imports at the top of your file so it's easy to see all the various modules your code will use in one place. 

Let's give it a try using the math module:
```
import math
```


This is the simplest way to import a module. By doing this we import the whole module in its entirety. Once you've done that, you can call functions in this module by using the name of the module, followed by a period, and the name of the function.

```
result = math.ceil(1.2) # 2
result = math.floor(1.2) # 1
result = math.gcd(144, 12) # 12
```

<div class="aside" markdown="1">

### The Dot Notation in Python

You'll see this dot notation all over in python. Whenever you find it, it's always an indication that the thing on the left contains the thing on the right, or conversely that the thing one right is part of the thing on the left. In this example, the `math` module contains the `gcd` function. 

</div>

That certainly works, but it can get a bit painful to constantly be typing `math` over and over again. In order to cut down on this, we can give the math module a new shorter name:

```
import math as m


result = m.ceil(1.2) # 2
result = m.floor(1.2) # 1
result = m.gcd(144, 12) # 12
```

If you only need one or two functions from a module, then there's no need to import the whole thing! We can import only the specific parts that we need:

```
from math import floor

result = floor(1.2) # 1
```

<div class="aside" markdown="1">

### Why Don't We Just Import Everything?

A good way to think of this is to think of our Python environment as our workbench and the Python modules as our tools. If you've only got to drill a hole in a board, there's no reason you'd need your soldering iron, jackhammer, or table saw to get the work done. Getting all those tools out will just waste time, and they'll clutter up your workbench. The Python environment works in the same way. The more modules we import, the more bloated and cluttered our code and memory will be. This results in code that takes up more memory and runs more slowly.

</div>

## Installing Third-Party Python Packages

If you can't find something in the standard Python libraries, there's still a good chance that it exists in the broader Python world. The best way to find other Python libraries is to visit the [Python Package Index (PyPI)](https://pypi.org).

Our python distribution (Anaconda) comes with an easy way to install other libraries, the `conda` command line utility. While you can't install everything with conda, it does a lot of work to make sure that all the extra packages we install will work together. 

Here's where that terminal at the bottom of the PyCharm IDE comes in handy! Let's install the popular Python data analysis library, Pandas.  In the terminal pane, type the following and press **return**:

`conda install pandas`

Conda will automatically find and download the right version of the pandas library. From then on, we can treat it like any other Python module. Just import it and you're free to start using it!

### What if A Package Isn't Available Through Conda?

Python itself comes with an easy way to install packages from PyPI, the command line utility `pip`. Installing a package with pip is very similar to installing a package with conda: 

`pip install pandas`
