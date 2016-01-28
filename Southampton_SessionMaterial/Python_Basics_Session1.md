> ## Learning Objectives {.objectives}
>
> *   Introducing Python and pip
> *   Introduction to running the Python interpreter
> *   Using Python interactively
> *   Introduction to Python variables
> *   Creating and Assigning values to variables
> *   Working with Arrays
> *   Basic program control - COnditionals and Loops
> *   Creating and Using Functions
> *   Using libraries

## Introducing Python

Python is a powerful, fast, open-source & easy to learn programming language - Python is ideal for first time programmers.
Python’s design philosophy has an emphasis on code readability, and its syntax allows programmers to express concepts in fewer lines of code than would be possible in languages such as C++ or Java.

The core philosophy of the language is summarized by [PEP 20(The Zen of Python)](http://www.python.org/dev/peps/pep-0020), which includes aphorisms such as:

- Beautiful is better than ugly.
- Explicit is better than implicit.
- Simple is better than complex.
- Complex is better than complicated.
- Readability counts.

In this course, we will be learning the basics of Python, in a **scientific data analysis**, **web scraping**  and **web development** contexts. For web development, we will be using a very simple web framework by the name of [Flask](http://flask.pocoo.org), which is 
very light weight and easy to use.

## pip

pip is a package management system used to install and manage software packages written in Python. We will be using pip to install things like Flask and any other dependencies we want to make use of. You should already have pip installed as per the course preparatory work.

## Running the Python interpreter

Normally, you write Python programs in a Python script, which is basically a file of Python commands you can run.
But to start with, we'll take a look at the Python interpreter.
It's similar to the shell in how it works, in that you type in commands and it
gives you results back, but instead you use the Python language.

It's a really quick and convenient way to get started with Python, particularly when learning about things like how to use variables, and it's good for playing around with what you can do and quickly testing small things.
But as you progress to more interesting and complex things you need to move over to writing proper Python scripts, which we'll see later.

You start the Python interpreter from the shell by:

~~~ {.bash}
$ python
~~~

And then you are presented with something like:

~~~ {.output}
Python 3.4.3 |Anaconda 2.3.0 (x86_64)| (default, Mar  6 2015, 12:07:41) 
[GCC 4.2.1 (Apple Inc. build 5577)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
~~~

And lo and behold! You are presented with yet another prompt.
So, we're actually running a Python interpreter from the shell - it's only yet another program we can run from the shell after all.
But shell commands won't work again until we exit the interpreter.

You can exit the interpreter and get back to the shell by typing:

~~~ {.python}
>>> exit()
~~~

...or alternatively pressing the Control and D keys at the same time.
Then you'll see:

~~~ {.output}
$ 
~~~

Phew - back to the shell!
