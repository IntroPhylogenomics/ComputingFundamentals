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

  - Numbers
    - Note that, unlike bash, Python can handle _both_ integers and floating point (decimal) numbers.
    - Integers - `myInt = 10`
    - Floating point numbers (decimals) - `myFloat = 3.21312`
    - Define myInt and myFloat as above. Now calculate `myInt / myFloat`. What type of number is the result?
    - Now try `float(myInt)` and `int(myFloat)`. What are the results? Look back at the values of `myInt` and `myFloat`. Have they changed?
    - Changing numbers from one type to another is one form of "type casting".
  - Strings - `myStr = "This is a string."`
    - Strings can be of any length, but are always defined with quotes.
    - Individual characters, or subsets of characters, can be accessed using square brackets - []
      - String indices (and all indices in Python) start at 0
      - `myStr = "biology"`
      - `myStr[0]`
      - A range of indices can be defined with a colon
      - `myStr[2:5]`
    - Strings can be concatenated together with the `+` operator.
      - `myStr = "biology"`
      - `newString = myStr + "_is_super_interesting"`
      - `newString`
  - Booleans - `True` or `False`
    - These variables can take the values `True` or `False` only.
      - `myBool = True`
    - These are the data types used in things like `if...else` statements and `while` loops.
    - Logical statements, like `myNum > 3` or `myStr == "test"`, return a boolean variable indicating the result of the comparison
    - In Python, the value of a Boolean can be reversed by preceding it with `not`.
