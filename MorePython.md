# More With Python

## If Statements

If statements in Python are similar in form to Bash, but simpler. The general form is

```
if <CONDITION>:
    <DO_THIS>
```

The `if` statement has to finish with a `:`. Also, in Python, the code block inside the `if` statement __must__ be indented. You can use either tabs or a certain number of spaces. When using spaces, you must use the __same__ number of spaces throughout your code. The official recommendations for Python style strongly suggest using 4 spaces, rather than tabs.

The syntax for logical tests is quite intuitive in Python. To test equality, use two equals signs, `==`.

`myStr == "some text"`

You can test if two things are _not_ equal with `!=`.

`myStr != "other text"`

`if` statements can be used on their own, but no code will be executed when the condition is false.

## If...Else Statements

To include code blocks that should be executed when the condition is false, you'll need to use an `if...else` statement. These have the general form:

```
if <CONDITION>:
    <DO_THING_WHEN_TRUE>
else:
    <DO_THING_WHEN_FALSE>
```
            
Sometimes, you'll want to test a series of conditions to decide what to do. In that case you could use a nested set of `if...else` statements:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
else:
    if nuc == "C":
        print("Nucleotide is a C.")
    else:
        if nuc == "G":
            print("Nucleotide is a G.")
        else:
            if nuc == "T":
                print("Nucleotide is a T.")
```      

However, you'll notice that this can get pretty cumbersome pretty quickly. Thankfully, python offers another, more compact, way to write this:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T"
    print("Nucleotide is a T.")
```
            
The `elif` statements stand for `else...if` and capture what we tried to do above with the nesting.

It is important to realize that as we've currently written these statements, nothing would happen if the variable `nuc` didn't have the value `A`, `C`, `G`, or `T`. This can be a big problem when accepting input from a user or file that might provide an unintended value. To capture these cases, it's always best to close with a simple `else`:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T":
    print("Nucleotide is a T.")
else:
    print("This is not a valid nucleotide!")
```

## Lists

We've now covered the simple variable types in Python: integers, floats, strings, and bools. However, there are several more complex types of variables that allow us to store and access multiple values. Perhaps the most versatile and common of these more complex types are lists. Lists are always specified using square brackets - `[]`.

Lists can contain an arbitrary number and type of simpler variables, but we often want to use only one type in a list so as not to get confused.

```
listOfNums = [1,2,3,4]
listOfFloats = [3.14, 2.0, 12.3]
listOfStrings = ["Ecology", "Evolution", "Systematics"]
listOfBools = [True, False, False, True]
```
   
Even after they are created, lists can be modified. Individual elements can be added using the `.append()` method:

```
listOfNums.append(5)
listOfStrings.append("Neurobiology")
```

Take another look at these lists

```
listOfNums
listOfStrings
```

Elements can be removed using a few different methods. Try

`listOfFloats.pop()`

What is returned? And what does the list look like now?

You can remove specific values from a list, regardless of their position, by using the `remove(<VALUE>)` method. What happens when you execute

`listOfBools.remove(False)`

How does the list change?

Lists can contain lists as elements. For instance, try this:

```
newList = []
newList.append([1,2,3])
newList.append([4,5,6])
newList.append([12,13,14])
```
What does `newList` look like now?

`newList`

You can also add all the _individual elements_ of one list to another.

```
newList = [1,2,3]
newList.extend([4,5,6])
newList.extend([12,13,14])
```

How does this version of `newList` differ from what you got when you used `append()`?

You can view or extract parts of a list by using indices and "slicing" the list (just remember that Python starts counting at 0!)

`newList[4:7]`

What values are returned? How do these relate to the indices you provided?

You can also alter individual elements of lists by using indices

```
newList
newList[2] = 100
newList
```

## For Loops

One of the nicest things about Python is the relationship between lists and `for` loops. If you have an existing list, you can quickly iterate across all of its elements using this syntax:

```
for num in newList:
    print("This number is: %d" % num)
```
            
If you still want to iterate over a series of integers, you can use the range() function.

```
for num in range(10):
    print("This number is: %d" % num)
```

## A Note About Copying Variables

Try this

```
firstNum = 2
secondNum = firstNum
firstNum = 5
firstNum
secondNum
```

How do `firstNum` and `secondNum` compare to each other? Now try this

```
firstList = [1,2,3]
secondList = firstList
firstList.extend([4,5,6])
firstList
secondList
```

How do `firstList` and `secondList` compare?

## Reading From Files

To read or write from a file, you'll first need to define the file name

`inFileName = "FileToRead.txt"`

However, this is just a string variable with the file name. We need to create an object that can actually read the contents of a file. Python has a built-in function to create a file object

`open(<FILENAME>,<MODE>)`

The `<FILENAME>` argument is just a string with the file's name (or path to the file). The `<MODE>` argument tells Python whether we are reading from a file (`r`), writing to a file (`w`), or appending to a file (`a`). To open up a new File object to read file contents, use syntax like this

`inFile = open(inFileName,'r')`
    
There are several useful methods associated with file objects, but one of the most commonly used is `readline()`. This method will read lines one-by-one from the file. Note that the end of line character (\n) is retained when the line is read in.

`firstLine = inFile.readline()`

Files opened for reading can be used in a `for` loop, as follows, to go through all the lines in the file

```
for line in file:
    print("Length of line is: %d" % (len(line)))
```
            
Note that `line` is just a variable name we've chosen to hold each line as we iterate through the file. You can use any variable name you choose, as with any other `for` loop.

## Writing to Files

Writing to a file is very similar to reading from a file. First, you define an output file name

`outFileName = "FileToWrite.txt"`
    
To create a file object to use for writing, we'll again use the `open()` function, but we'll specify `'w'` for the `<MODE>`.

`outFile = open(outFileName,'w')`

To write to the file line-by-line, we can use the `.write()` method.

`outFile.write("This is a new sentence.\n")`

Note that the `write()` method does NOT, by default, add a new line character to strings. If we want to end a line, we have to explicitly include `\n`.

## Command-line Arguments

As with bash scripts, Python scripts can also take advantage of command-line arguments. To easily handle command-line arguments, we're going to take advantage of some functions in the `sys` library. So we'll need to start by importing that library:

`import sys`

Any command-line arguments we pass to a script can then be accessed using the `sys.argv` variable. For instance

`print(sys.argv[2])`
    
> _Practice Exercise_
>
> (1) Create a Python script that loads the `sys` library
>
> (2) Include the print statement above
>
> (3) Execute the script with several command-line arguments (`myScript.py one 2 THREE 4 five SIX`)
>    
> Which argument is printed when you run the line above?

We can also loop through all command-line arguments:

```
for arg in sys.argv:
    print(arg)
```
            
These abilities are very useful in a variety of contexts, but particularly when a set of filenames are provided as command-line arguments and you want to iteratively process each file.

## References

[Python for Beginners](https://www.python.org/about/gettingstarted/)

[Python Style Guide](https://www.python.org/dev/peps/pep-0008/)

[Codecademy Python Course](https://www.codecademy.com/learn/learn-python)
