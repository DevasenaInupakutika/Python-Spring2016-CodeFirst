## Flask and GET/ POST requests

By now, since we have an intermediate knowledge of the `Python` programming language. We'll be using `Flask`, a Python web application framework, to create a simple web application from scratch, with `MySQL` as a back end.

#### Introduction 

The de facto framework that usually comes to our mind is the `Django` framework when we think about Python. But from a beginner's perspective, Flask is easier to start with, as compared to Django.

Flask is a framework for building lightweight web applications. In order to get up and running, we will follow the instructions as mentioned below:

Setting up Flask is pretty simple and quick. With `pip` package manager, all we need to do is:

`pip` can be installed with below command:

~~~{.python}
easy_install pip
~~~

~~~{.python}
pip install flask
~~~

Now, let's create a baseline Flask application called `hello.py` as below by importing the `flask` module and create an app using Flask:

~~~{.python}
from flask import Flask
app=Flask("HelloApp")
~~~

Now define the basic route `/` and its corresponding request handler:

~~~{.python}
@app.route("/")
def hello():
    return "Hello World!"
~~~

Next, check if the executed file is the main program and run the app:

~~~{.python}
if __name__ == "__main__":
    app.run() 
~~~

Save the changes and execute `hello.py`:

~~~{.python}
python hello.py
~~~

Point your browser to [http://127.0.0.1:5000/](http://127.0.0.1:5000/) and you should see the welcome message.

#### Flask routes and decorators

You may be wondering what `@?app.route?stands` for and why we are using it. This is what is known as a **d?ecorator**.? 

The concept of decorators exists in most programming languages; their purpose is to inject or modify code in functions. 

In simpler terms, imagine you would like to do something at the entry and/ or exit points of a function. 
This is what is happening here ? `@app.route`, ?which is part of Flask, is doing some things internally for us so that we can accept a request coming from the user's browser into the Python. 

A *decorator* always starts with the **@** sign and goes on the line right before a function is defined.

### Flask: Taking parameters from the URL

Let's look at the code below:

~~~{.python}
from flask import Flask

app=Flask("My App")

@app.route("/")
def hello():
      return "Hello World!"
      
@app.route("/<name>")
def hello_someone(name):
      return "Hello {0}!".format(name.title())
      
app.run()
~~~

The **<name>** is a URL matcher - It will match **/** followed by any word, for example /andreas, /rachel etc. Flask will make this value available as a parameter to **hello_someone**. We then use the **name** variable to say hello to a particular user. 

We will edit the previous file and add the function **hello_someone**. And then check if that works by visiting URL [http://127.0.0.1:5000/andreas](http://127.0.0.1:5000/andreas) or your name if you prefer.

##### Challenge 1

Try and make the above program so that visiting **localhost:5000/bye/andreas** returns `Goodbye Andreas` or `Goodbye` for any other name given.

### Serving HTML using Flask

Flask lets us serve our HTML - This is possible using the **render_template** function. All we have to do is provide the name of the template and the variables we want to pass to the template engine as keyword arguments. 

Below is an example of how to render a template:

~~~{.python}
from flask import Flask
from flask import render_template

app=Flask("HelloApp")

@app.route("/")
def hello():
      return render_template("hello.html")
      
@app.route("/<name>")
def hello_someone(name):
      return render_template("hello.html", name=name.title())
      
app.run()      
~~~

**Note: Flask will look for templates in the templates folder.**
Flask uses another library called [Jinja2](http://jinja.pocoo.org/docs/dev/), which is a templating language for Python. It's extremely powerful. Here's what an example **html file hello.html** would look like, inside a templates folder, that uses Jinja2:

~~~
<!doctype html>
<title>Hello from Flask</title>
{% if name %}
    <h1>Hello {{ name }}! </h1>
{% else %}
    <h1>Hello World! </h1>
{% endif %}
~~~

##### Challenge 2

Extend the above code so that you can say goodbye to someone if you visit **localhost:5000/goodbye/<username>**.

Also, try to add some more parameters to the URL and pass those onto your `hello.html` template. May be something like "Hello <username>! Have a nice day!" and "Hello <username>! Have a good night!" corresponding to localhost URLs.

### Creating a home page

When the application runs for the first time, we should show a home page

