# Bash Scripting

One of the most useful and powerful aspects of working at the command line is that commands can be stored in special files, called scripts, which can then be executed all at once. This feature makes command-line workflows reproducible and transparent. Scripts are a critical tool for phylogenomics. Script files are not required to have any particular names, but by convention most people use the extension `.sh` for bash scripts. Bash is the specific type of Unix shell that we are using in this workshop, and is the default on most Mac and Linux systems.

# Shebang

The first line in a script file has a very special meaning that tells the system how to interpret all the other commands in the file. This line starts with "#!" - also known as a shebang. The shebang tells Terminal that we're about to indicate which language (shell) we're going to use. Don't worry too much about the syntax, but we will follow the shebang with this line to indicate that this is a bash script

`#! /usr/bin/env bash`

Whenever you start to create a bash script, the first thing you do should always be to include this line at the top.

> __Practice__
>
> (1) Use `nano` to create a new script file called `myScript.sh`
>
> (2) Add the shebang line at the top
>
> (3) Save the file and quit `nano`

# Permissions

If you list the files in a directory with the long flag on (`ls -l`) you can see a lot of information about each file. The first 10 characters on each line may seem mysterious, but they tell you about the permission settings for each file and directory. The first character simply indicates whether that thing is a file (`-`) or a directory (`d`). Every file and directory has three types of permissions

- Read (`r`)
- Write (`w`)
- Execute (`x`)

and there are three groups whose permissions can be controlled separately

- Owner
- Group
- Others

So the next 9 characters indicate what permissions (`rwx`) are allowed for each of the groups. The first three characters correspond to the user, the next three to the user's group, and the last three to everyone else (others). More information on permissions is [available on Wikipedia](https://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions).

The permission that is important for scripts is the execute (`x`) permission. In order to run the commands in a script, this must be on (you need to see an `x` in the 4th character if you own the file). By default, execute permissions are not granted to new text files. To adjust permissions, you can use the `chmod` command. For instance, to add execute permissions for the user (i.e., you), you can use

`chmod u+x myScript.sh`

> __Practice__
> 
> (1) Check the permission settings on the file you created above (`myScript.sh`).
>
> (2) If needed, add execute permissions to this file.

# Commenting

Inside a bash script, or any other program, it is useful to leave comments as you write commands. These comments should explain what you are intending to do with your commands, so that you can remember later or that someone else can understand just by looking at your file. There is no limit on the number of comments that can be included in a script, and a good rule of thumb is to always write a little more than you think is necessary at the time.

Comments are indicated in scripts using the `#` character. Anything that follows this character on the same line will be ignored. Here's a very simple script that illustrates the use of comments.

```
#! /usr/bin/env bash

# This is my first line of comments. This line only contains comments.

echo "script works!" # This is a comment that follows a command.
```

If executed, this script should just print "script works!" back to the Terminal screen. Note that we've used a new command in this script - `echo`. This is a simple command to print a string to the screen. Any argument that follows `echo` will be printed.

To execute a script, simply type the path (relative is usually easiest) to that file on the command line. For instance, if `myScript.sh` is in your current working directory, you can type

`./myScript.sh` - Executes `myScript.sh`

Remember that `.` is just shorthand for the current working directory.

> __Practice__
>
> (1) Add the lines above to your file, `myScript.sh`.
>
> (2) Run your script and verify that it produces the expected output.

# Variables

Storing and accessing values with variables is one of the most important skills when writing scripts. To store a value in a variable, use the assignment operator - `=`. 

`myVar=2`

Here, our variable name is `myVar` and we're assigning it the value `2`. Note that Bash, unlike some other programming languages, does not allow spaces between the variable name, the assignment operator, and the value.

To display the value of a variable, we can use the `echo` command. Note that to access a variable's value, we need to precede the variable's name with a `$`,

`echo $myVar`

Different kinds of values can be stored in a variable, not just numbers

`myVar="test"`

In this case, we've stored a string - `"test"`. Strings are named as such, becuase they store strings of characters.

Also, note that echo statements can include multiple values back-to-back, including literal strings. One way in which this is useful is to include a literal string that describes what value is being printed

`echo "The value of myVar is "$myVar`

> __Practice__
>
> (1) Create a new varilable (`myVar`) in your script and assign it a value.
>
> (2) Include an echo statement in your script to print the value of this variable to the screen.

# Math in Bash

In general, bash isn't very good for mathematical operations, but it can be done in several ways. Probably the easiest is to wrap a mathematical expression in _double_ parentheses and precede it with a `$`, since you pretty much always want the _value_ of the mathematical result.

- `echo $(( 2 + 2 ))`
  - `myNum = $(( 2 + 2 ))`
- `echo $(( 3 * 6 ))`
- `echo $(( 20 / 3 ))`
- `echo $(( 20 % 3 ))`

Compare the output of these last two lines? What's going on?

NOTE: bash can only handle _integers_ and not floating-point numbers (i.e., decimals)

Try this. What happens?

    - `myVar=3`
    - `echo $myVar`
    - `((myVar++))`
    - `echo $myVar`
    - `((myVar++))`
    - `echo $myVar`

What does the `++` operator do?

# Command-Line Arguments

Often you may want to write a script that does different things depending on the values of certain variables. While you could manually edit your scripts for each condition you want to run, a more convenient thing to do is to write one single script that you can run in different ways depending on arguments passed to it on the command line. Conveniently, bash has reserved certain special variable names for this very purpose.

Remember that to access the value of a variable, we precede it with `$`. So, to access the value of the first command-line argument, we use `$1`. For the second command-line argument, we use `$2`, etc. The simplest thing to do in a script is to just print the values of these variables back to the screen.

`echo $1`

But we can also use the values of these variables to make our script behave in different ways (more below).

> __Practice__
>
> (1) Add lines in your script to seperately print out the first and second arguments passed to the script on the command line.

# For Loops

One of the most common reasons to write a script is to automate something that is, at a minimum, very tedious to do manually and, at worst, completely impossible otherwise. A versatile way to incorporate repitition into a script is to use a `for` loop. `for` loops in bash have the following structure:

```
for num in 1 two 3 FOUR
do
  echo $num
done
```

Let's break this down. First, we've defined a new variabled named `num`. This variable can be named anything you want. In this case, `num` will iteratively take the value of anything included in the list that follows `in`. During each iteration, the code in between `do` and `done` will be executed. In this case, we will simply print out each of the values our variable takes, one after the other. Later, we will use `for` loops that have a whole series of commands inside the loop.

> __Practice__
>
> (1) Add the for loop written above to your script and see how it behaves.
>
> (2) Now add a new element to the list of values after `in` and see what happens.

Double parentheses notation can also be used to write a `for` loop in a way that doesn't require you to write out every unique element in the list:

```
for ((num=1;num<=10;num++))
do
  echo $num
done
```

When written this way, the `for` loop statement has a structure like this

```
for (( <START_VALUE> ; <STOP_CONDITION> ; <LOOP_UPDATE> ))
```

The variable is initialized to the start value, updated according to the loop update, and continues until the stop condition is no longer true. The loop update (`num++`) here adds `1` to `num` each time the loop iterates. NOTE: You _don't_ precede variables with `$` inside double parentheses.

Sometimes you'll want to loop through a whole series of command-line arguments. To loop through these arguments, you can write `$@` in place of the list in your `for` statement.

```
for num in $@
do
  echo $num
done
```

> __Practice__
>
> (1) Add an echo statement to your script to indicate that you're about to write out the command-line arguments.
>
> (2) Add the for loop written above to your script and run your script with some command-line arguments.

# Backticks

Variables can be used to store values output from other bash commands. However, you need to tell bash to execute the other commands first so that their values can be stored in the variable. To do this, you can surround the commands in backticks - `` ` ``.

```
myWordLength=`echo -n "testWord" | wc -m`
```

To break this down, we're first using `echo` with the `-n` flag to print `testWord` without a newline character at the end. We're then using a pipe - `|` - to send the output into the word count command - `wc`. The `-m` flag tells `wc` to only count characters. By surrounding these commands in backticks, the output (`8`) is stored in the variable `myWordLength` rather than being printed to the screen.

# If...Else

One of the other very important programming concepts is known as "flow control". Basically, this just means doing different things depending on current conditions. There are several ways to accomplish flow control, but probably the most common is the `if...else` statement, which looks like this:

```
if <TEST_SOMETHING>
then
  <DO_THING_1>
else
  <DO_THING_2>
fi
```

There are lots of different ways to compare values, depending on what type of values you're working with. Here is a page that lists several options: [Bash comparison operators](http://tldp.org/LDP/abs/html/comparison-ops.html). Here's one example:

```
# Defining value of numeric variable
a=2
        
# if...else to see if value of number is at least 3
if [ $a -lt 3 ]  # Note: this could also be ((a < 3))
then
  echo "$a is less than 3."
else
  echo "$a is NOT less than 3."
fi
```

Here's an example of combining backticks, command-line arguments, and an if...else statement to write a script that tests if a command-line argument has a certain number of characters.

```
# Recording length of word provided on command line
# What's going on with the backticks (``) here?
myWordLength=`echo -n $1 | wc -m`

# test if word is at least 5 characters
if [ $myWordLength -lt 5 ]
then
  echo "$1 is shorter than 5 characters."
else
  echo "$1 is at least 5 characters in length."
fi
```

# While Loops

Another flow control structure is a `while` loop. A `while` loop just has a single condition that it waits to be satisfied before exiting. `while` loops are somewhat more flexible than `for` loops, because they can run for a variable number of iterations, depending on the conditions. __WARNING:__ Because `while` loops don't have a fixed number of iterations, they can run infinitely if you're not careful.

```
num=1                     # Initialize num to 1
while [ $num -lt 11 ]     # Keep going as long as num is less than 11
do
  echo $num               # Print num
  (( num++ ))             # Increment num by 1
done
```
        
# Reading Lines from a File

Bash has special syntax that can be used in combination with a while loop to keep reading lines from a file. In this case, the name of the file to be read is passed as the first command-line argument (`$1`).

```
while read line
do
  echo $line
done < "$1"
```

# Reading Values Interactively

You can accept values directly from users by using `read`. In general, you'll want to prompt the user, then follow the prompt with `read <VARIABLE>`. Whatever the user types in will be stored in that variable. Here's basic usage:

```
echo -n "Please type your name: "
read name
echo "Hello, "$name
```     

Here's an application that uses a while loop:

```
echo "Try to guess the word I'm thinking of: "
read word
while [ $word != "tigers" ]
do
  echo "Try again to guess the word: "
  read word
done
echo "You finally got it!"
```

