# Python Basics

## What is Python?

Python is an interpreted, high-level programming language that is very popular among computational biologists. An interpreted language is one that is not compiled before running. Instead, an interpreter executes a human-readable text file. Roughly speaking, a high-level language is one that abstracts away the details of the computer hardware, to make the code easier for a person to write and understand. Python is probably the most "human readable" programming language. It's also one of the few languages where line indentation is actually interpreted as part of the code. Python is _much_ less picky than bash about spacing within lines, though. Python is also a dynamically typed language. As we create variables, we don't need to specify exactly what kinds they are. Python figures this out on the fly.
  
## Running Python

Unix-based operating systems typically come with Python pre-installed. To check if you have a version of Python, go to the command line and type

`python`

This command will open the Python interpreter if it's installed. You should see a new kind of command prompt (`>>>`). You will remain inside the Python interpreter until you quit

`quit()`

In the header lines displayed when you start the Python interpreter, you should see a particular vesrion number. Note that there are some important differences between Python 2 and 3. If you end up using Python libraries in your research, they may require use of a particular version of Python.

## Basic Python Data Types

Even though we don't have to explicitly list a type when we create a variable in Python, there are distinct data types and we need understand their differences.

#### Numbers

Note that, unlike bash, Python can handle _both_ integers and floating point (decimal) numbers. To create an __integer__, assign a value without a decimal to a variable

`myInt = 10`

To create a __floating point number__, assign a value that includes a decimal

`myFloat = 3.21312`

> _Practice Exercise_
>
> Define `myInt` and `myFloat` as above. Now calculate `myInt / myFloat`. What type of number is the result?
>
> Now try `float(myInt)` and `int(myFloat)`. What are the results? Look back at the values of `myInt` and `myFloat`. Have they changed?
>
> Changing numbers from one type to another is one form of __type casting__.
    
#### Strings 

Strings are variables that contain a series (or string) of characters. They can be assigned values that are wrapped in quotation marks.

`myStr = "This is a string."`

Strings can be of any length and can include spaces or other special characters.

Individual characters, or subsets of characters, can be accessed using square brackets (`[]`) but note that string indices (and all indices in Python) start at 0. For instance, try

`myStr[0]`

A range of indices can be defined with a colon to extract a series of characters

`myStr[2:5]`

Strings can be concatenated together with the `+` operator.

`myStr = "biology"`
`newString = myStr + "_is_super_interesting"`
`newString`
 
      
#### Booleans

Booleans are variables that can take the values `True` or `False` only.

`myBool = True`

Note that `True` and `False` need to be written exactly like that, with only the first letter capitalized. Booleans are commonly used in flow control structures like `if...else` statements and `while` loops. Logical statements, like 

`myNum > 3` or 

`myStr == "test"`

return a boolean variable indicating the result of the comparison.

In Python, the value of a Boolean can be reversed by preceding it with `not`.

`not myBool`

## String Formatting

Python has a special way to format strings so that the values of variables can be included in the string itself. The operator `%` is used to indicate that the values of certain variables should be used to fill in a string. The parts of the string where the values should go is indicated with placeholders. The three most basic placeholders are:

- `%d` - An integer
- `%f` - A floating point number (i.e., a decimal)
- `%s` - A string
    
> _Practice Exercise_
>
> `faveInt = 7`
>
> `faveFloat = 3.14`
>
> `faveString = phyleaux`
>
> `print("Favorite integer is %d, favorite float is %f, and favorite string is %s." % (faveInt,faveFloat,faveString))`
>
> Note how the variables holding the values are provided in the same order inside parentheses after the `%`.

## Functions

Functions are the verbs of a programming language. Functions take some variables or objects as input (arguments) and either do something with them or return a new variable/object. Functions are always written like this

`myFunction(object1,object2,...)`

Functions _always_ have parentheses, even if they don't need any arguments to be passed to them. For example

`myFunction()`

The number and type of arguments needed is specific to each function. Perhaps the simplest function to use is

`print()`

`print()` can take an arbitrary number of variables as arguments and will print them to the screen.

`print("testString")`

`print("testString",2)`

Here are a few other really useful functions and descriptions of what they do

`len(string)` - Takes one argument (a string) and returns its length

`abs(number)` - Takes one argument (either an integer or a float) and returns its absolute value

`round(float)` - Takes one floating point number as an argument and rounds it to the nearest integer

`type(variable)` - Takes one variable as an argument and returns its type

> _Practice Exercise_
>
> (1) Assign a string to a variable
>
> (2) Calculate the length of the string
>
> (3) Print the length to the screen
>
> Can you accomplish (2) and (3) in one line?

## Methods

Methods are functions that belong to a variable. Methods are called by appending them to the name of a variable, separated by a `.` For instance, let's say we define a string

`myStr = "biOLogy  "`

Here are some really useful methods that can be used with that string:

`myStr.upper()` - Converts all characters in the string to uppercase
`myStr.lower()` - Converts all characters in the string to lowercase
`myStr.strip()` - Removes whitespace from the beginning or ending of the string

Methods can also be chained (called consecutively).

`myStr.strip().lower()`
`myStr.replace("y","ical")`

This method functions like find and replace, where the first argument is the text to find and the second argument is the text to use when replacing.

`.split(char)` breaks up a string using the character provided as an argument as the delimiter. This method then returns a list of new strings. We'll talk more about lists later.

`myStr.split("O")`

If you are unsure what methods are available for a given variable, you can use

`dir(myVar)`

 Note that methods starting and ending with "__" are not meant for users to call. They are methods to be used by the system.

> _Practice Exercise_
>
> (1) Create a string variable (`myStr`).
>
> (2) Show the available methods with `dir(myStr)`.
>
> (3) Pick a method that you haven't used before and see what it does with `myStr`.

## Creating a Python Script

Python scripts can be created in a similar way to bash scripts. Open a blank text file and add a "shebang" line at the top. This time, list `python` instead of `bash`.

`#!/usr/bin/env python`

Add some Python code to the file and save it (`myScript.py`). For instance, you can try printing something to the screen with `print()`.

To be able to execute the script, you'll need to add execute permissions to the file with `chmod` as you did with Bash scripts.

`chmod +x myScript.py`

Now try executing the script in Terminal

`./myScript.py`

You can also execute a Python script without adding execute permissions by passing it to the Python interpreter

`python myScript.py`

## Comments in Python

Comments are included in Python, like Bash, by putting a `#` at the beginning of a line (or part of a line). Many text editors have a shortcut keystroke to toggle lines between being commented and uncommented.

`# This is an example of a comment`

## Additional Resources

- [Python](https://www.python.org)
- [Software Carpentry - Intro. to Python](http://swcarpentry.github.io/python-novice-inflammation/)
