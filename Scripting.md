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

# Command-Line Arguments

Often you may want to write a script that does different things depending on the values of certain variables. While you could manually edit your scripts for each condition you want to run, a more convenient thing to do is to write one single script that you can run in different ways depending on arguments passed to it on the command line. Conveniently, bash has reserved certain special variable names for this very purpose.

# For Loops
