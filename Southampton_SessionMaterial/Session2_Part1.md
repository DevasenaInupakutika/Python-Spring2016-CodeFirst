## Processing Data

## Learning Objectives {.objectives}
*   Write a script to open a data file and print out its contents.
*   Perform some operations on strings to extract desired data from it.
*   Understand the basics of how Python handles objects.

So far we've seen how to use and manipulate variables, and how to use loops in a script to process strings.
But let's take a look at a more interesting use case - performing some operations on the data in our CSV data file.

We'll start out by looking at how to read the data file and print
its contents in a script, and then modify our script to perform
some conversions and output that. Along the way, we'll see how we can make our code more understandable to 
others (as well as ourselves, when we might come back to it at a later date).

## Printing contents of a data file

We first need to be able to read in our `Annual mean temperature records 1910-2014` data picked from *Scottish Environment Statistics Online - National Climate Information Centre (Met Office)*.  The data is present in file `CCtemperature.csv`. We will be reading our data from this file, and using a loop, print out each line. Let's write another script called `temp_analysis.py`, and enter the following:

~~~ {.python}
temp_data = open('../data/CCtemperature.csv', 'r')

for line in temp_data:
    print(line)
~~~

Using `open`, we first specify the file we wish to open, and then include how
we want to use that file. If we wanted to open a file to write to, we would use 'w', but in this case, we specify `r` for reading.

In general, we know that a loop will iterate over a collection and set a loop
variable to be each item in that collection. When Python deals with files, it
does something quite helpful in a loop. By specifying `climate_data` as our collection, it reads in a single line at a time from our data file, assigning it to our `line` loop control variable.

We can run our code with:

~~~ {.bash}
$ python temp_analysis.py
~~~

And we get the following output:

~~~
Year,Average surface temperature (degrees Celsius),Differences from 1961-1990 average (degrees Celsius)

1910,6.95,-0.08

1911,7.6,0.57

1912,6.97,-0.06

1913,7.43,0.4

1914,7.36,0.33

1915,6.48,-0.55

1916,6.92,-0.11

1917,6.41,-0.62

1918,6.95,-0.08

1919,6.18,-0.85

1920,7.23,0.2

1921,7.72,0.69

1922,6.43,-0.6

1923,6.65,-0.38

1924,7.01,-0.02

1925,6.88,-0.15

1926,7.31,0.28

1927,6.76,-0.27

1928,6.92,-0.11

1929,6.75,-0.28

1930,6.94,-0.09

1931,6.89,-0.14

1932,7.25,0.22

1933,7.81,0.78

1934,7.69,0.66

1935,7.14,0.11

1936,7.15,0.12

1937,6.99,-0.04

1938,7.74,0.71

1939,7.4,0.37

1940,6.86,-0.17

1941,6.72,-0.31

1942,6.82,-0.21

1943,7.6,0.57

1944,7.22,0.19

1945,7.93,0.9

1946,7.17,0.14

1947,7,-0.03

1948,7.48,0.45

1949,7.95,0.92

1950,6.94,-0.09

1951,6.76,-0.27

1952,6.6,-0.43

1953,7.93,0.9

1954,6.86,-0.17

1955,7.03,0

1956,6.88,-0.15

1957,7.5,0.47

1958,6.93,-0.1

1959,7.88,0.85

1960,7.26,0.23

1961,7.29,0.26

1962,6.59,-0.44

1963,6.4,-0.63

1964,7.18,0.15

1965,6.44,-0.59

1966,6.66,-0.37

1967,7.16,0.13

1968,6.8,-0.23

1969,6.79,-0.24

1970,6.86,-0.17

1971,7.7,0.67

1972,6.98,-0.05

1973,7.14,0.11

1974,7.16,0.13

1975,7.53,0.5

1976,7.45,0.42

1977,6.89,-0.14

1978,6.95,-0.08

1979,6.2,-0.83

1980,7.09,0.06

1981,6.8,-0.23

1982,7.4,0.37

1983,7.51,0.48

1984,7.38,0.35

1985,6.51,-0.52

1986,6.42,-0.61

1987,6.74,-0.29

1988,7.52,0.49

1989,7.67,0.64

1990,7.82,0.79

1991,7.42,0.39

1992,7.32,0.29

1993,6.87,-0.16

1994,7.18,0.15

1995,7.49,0.46

1996,6.95,-0.08

1997,8.04,1.01

1998,7.58,0.55

1999,7.73,0.7

2000,7.6,0.57

2001,7.36,0.33

2002,8.02,0.99

2003,8.21,1.18

2004,8.12,1.09

2005,8.09,1.06

2006,8.23,1.2

2007,8.18,1.15

2008,7.67,0.64

2009,7.84,0.81

2010,6.54,-0.49

2011,8.06,1.03

2012,7.32,0.29

2013,7.52,0.49

2014,8.45,1.42
~~~

Hmmm... but that's not really perfect, since it's also printing out additional
newlines which exist at the end of each line in our data file.
We can remove them by stripping them out, using `rstrip`, a function
that works on strings. We can use it like:

~~~ {.python}
    print(line.rstrip())
~~~

## Python and object orientation - in a nutshell {.callout}
 
So far we've used strings, which are a type of object in Python.
In general, an object is an instance of something called a class.

A class defines how a certain thing can behave, and an object
is then a particular thing that behaves the way its class tells it to.
You can define classes that include properties (like variables, associated
with that class), and methods (like functions, also associated with
that class and can perform operations on them). We can use classes to
define things in the real world.

For example, a car is made up of things like an engine, wheels, windows,
and so forth - these things could be defined as classes. And for
each of these, they would have their own properties and methods. A wheel class
for example, could have diameter and width as properties, and a window
could have size, tint and shape and properties, and assuming it's an 
electric window, it could have up() and down() as methods to raise
and lower the window. A class can have as many properties and methods
as we choose to define for it.

When we define a particular car, we could say it has a single engine,
four wheels and four windows. Each of these would be an object --- an instance
of its class --- each with its own set of properties, which could all
be different. We're taking advantage of the fact that all four
windows and all four wheels will behave the same way, but individually.
Using the down() method on one of the windows would cause
that window to lower, but only that window.

So, in our example, `line` is a String object, an instance of a String class.
And that String class has a defined method called `rstrip()`, which 
removes the trailing newline. There are many other String methods which
are incredibly useful!

So, let's try that out:

~~~ {.python}
temp_data = open('../data/CCtemperature.csv', 'r')

for line in temp_data:
    print(line.rstrip())
~~~

And now we get:

~~~
Year,Average surface temperature (degrees Celsius),Differences from 1961-1990 average (degrees Celsius)
1910,6.95,-0.08
1911,7.6,0.57
1912,6.97,-0.06
1913,7.43,0.4
1914,7.36,0.33
1915,6.48,-0.55
1916,6.92,-0.11
1917,6.41,-0.62
1918,6.95,-0.08
1919,6.18,-0.85
1920,7.23,0.2
1921,7.72,0.69
1922,6.43,-0.6
1923,6.65,-0.38
1924,7.01,-0.02
1925,6.88,-0.15
1926,7.31,0.28
1927,6.76,-0.27
1928,6.92,-0.11
1929,6.75,-0.28
1930,6.94,-0.09
1931,6.89,-0.14
1932,7.25,0.22
1933,7.81,0.78
1934,7.69,0.66
1935,7.14,0.11
1936,7.15,0.12
1937,6.99,-0.04
1938,7.74,0.71
1939,7.4,0.37
1940,6.86,-0.17
1941,6.72,-0.31
1942,6.82,-0.21
1943,7.6,0.57
1944,7.22,0.19
1945,7.93,0.9
1946,7.17,0.14
1947,7,-0.03
1948,7.48,0.45
1949,7.95,0.92
1950,6.94,-0.09
1951,6.76,-0.27
1952,6.6,-0.43
1953,7.93,0.9
1954,6.86,-0.17
1955,7.03,0
1956,6.88,-0.15
1957,7.5,0.47
1958,6.93,-0.1
1959,7.88,0.85
1960,7.26,0.23
1961,7.29,0.26
1962,6.59,-0.44
1963,6.4,-0.63
1964,7.18,0.15
1965,6.44,-0.59
1966,6.66,-0.37
1967,7.16,0.13
1968,6.8,-0.23
1969,6.79,-0.24
1970,6.86,-0.17
1971,7.7,0.67
1972,6.98,-0.05
1973,7.14,0.11
1974,7.16,0.13
1975,7.53,0.5
1976,7.45,0.42
1977,6.89,-0.14
1978,6.95,-0.08
1979,6.2,-0.83
1980,7.09,0.06
1981,6.8,-0.23
1982,7.4,0.37
1983,7.51,0.48
1984,7.38,0.35
1985,6.51,-0.52
1986,6.42,-0.61
1987,6.74,-0.29
1988,7.52,0.49
1989,7.67,0.64
1990,7.82,0.79
1991,7.42,0.39
1992,7.32,0.29
1993,6.87,-0.16
1994,7.18,0.15
1995,7.49,0.46
1996,6.95,-0.08
1997,8.04,1.01
1998,7.58,0.55
1999,7.73,0.7
2000,7.6,0.57
2001,7.36,0.33
2002,8.02,0.99
2003,8.21,1.18
2004,8.12,1.09
2005,8.09,1.06
2006,8.23,1.2
2007,8.18,1.15
2008,7.67,0.64
2009,7.84,0.81
2010,6.54,-0.49
2011,8.06,1.03
2012,7.32,0.29
2013,7.52,0.49
2014,8.45,1.42
~~~


