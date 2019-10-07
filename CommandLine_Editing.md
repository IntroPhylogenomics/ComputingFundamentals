# Editing Files and Folders from the Command Line

## Copying, Moving, and Renaming

You will often need to copy or rename a file from the command line. To copy a file inside your current working directory, you can use the copy command - `cp`. For instance, if you want to make a copy of a data file for a new analysis, you could use

`cp myData.txt myNewData.txt` - copy a file

You can also make copies that end up in other folders by adding a relative or absolute path before the filename

`cp myData.txt ../myNewData.txt` - copy data to the parent of current working directory

Moving and renaming files uses the same command - `mv`. If the source and destination filenames are in the same folder (e.g., the current working directory) then `mv` will simply rename the file

`mv myData.txt myOldData.txt` - rename `myData.txt` to `myOldData.txt`

However, if the source and destination filenames reference different folders, then `mv` will move the file

`mv myData.txt ..` - move `myData.txt` to parent of current working directory

You can also use `mv` to simultaneously move and rename a file

`mv myData.txt ../myOldData.txt` - both moves and renames myData.txt

## Creating New Files and Folders

To create a new file on the command line, there are a few options. The easiest is to use the `touch` command. For instance, to create a new file called `test.txt`, you could use

`touch test.txt` - create `test.txt`

This will create a new, empty text file called test.txt in your current working directory. You can also provide a path (absolute or relative) in the argument to `touch` to specify another location, for example

`touch Desktop/test.txt` - create `test.txt` in the `Desktop` folder

The equivalent command for creating a new folder is `mkdir`. To create a new, empty folder in the current working directory, type

`mkdir myFolder` - create new folder called myFolder.

Files, but not folders, can also be created by using one of text editors available directly through the command line. Probably the simplest of these editors is called `nano`. To start `nano`, simply type its name

`nano` - open the `nano` text editor

Note that when you start `nano`, your Terminal will change appearance so that you no longer see the standard command line. Instead, you will be inside a `nano` editing window. As you type, your text will be added to your text file as it would in any other program. You should also see a series of available commands at the bottom that start with `^`. That symbol simply indicates that you should hold down the control button and then the relevant letter to execute that command. For instance, to save your text file without quitting `nano`, hold down control and type `o` (lowercase is fine). You will then be prompted to enter a filename. When you're ready, press return and the file will be saved with that name. To exit `nano` and return to the standard command prompt, hold down control and type `x`.

Other, more advanced, text editors like `vi` and `emacs` are also available on many Unix systems, but we won't need their functionality for this course.

## Viewing and Editing File Contents

In addition to creating new files, `nano` can be used to edit existing files. To do this, simply add the name of the file as a command-line argument

`nano myFile.txt` - open `myFile.txt` in `nano` for editing

A list of keyboard shortcuts for `nano` can be found [here](https://www.nano-editor.org/dist/latest/cheatsheet.html).

Sometimes you may also want to just view the contents of a text file (or series of files) without opening an editor. The simplest command to do this is `cat`

`cat test.txt` - view the entire contents of `test.txt`

You can download a copy of [test.txt here](https://github.com/IntroPhylogenomics/ComputingFundamentals/blob/master/test.txt).

When you execute this command, the file's contents will be printed to the Terminal screen. You can also list the contents of multiple files at the same time using a wildcard. For instance, if you want to view the contents of all text files at once, you can use

`cat *.txt` - view the contents of all files ending with `.txt`

This ability is actually where `cat` derives its name - from con__cat__enating the contents of a series of files.

While `cat` is very useful, sometimes you don't want to view all the contents of a file at once. You may only want to view a few lines at the very beginning or end of a file. In these cases, the commands `head` and `tail` are what you want. For instance, to view the first 10 lines of a file you can use

`head test.txt` - view the first 10 lines of `test.txt`

The precise number of lines that are displayed can be adjusted using the `-n` flag for `head`. For instance, to see the first 20 lines, use

`head -n 20 test.txt` - view the first 20 lines of `test.txt`

The `tail` command works similary to `head`, but instead starts at the end of the file. For instance, try

`tail test.txt`

As with `head`, you can adjust the number of lines displayed by `tail`

`tail -n 20 test.txt`

You can also scroll through the contents of a file interactively using `less`. If you open a file with `less`, you can use the up and down arrows to move through the file. Pressing `q` at any point will exit `less` and bring you back to the standard Terminal screen.

`less myFile.txt`

If you need an example text file to use with `less`, you can copy the text from this tutorial and save it locally on your computer. 

## Searching Through Files

Sometimes you may want to see if a certain text pattern exists in a file without viewing the entire file. In this case, the `grep` command is incredibly powerful. The basic syntax is

`grep <PATTERN> <PATH_TO_FILE>`

For instance, to search for the string `five` in the file `test.txt`, we could use

`grep five test.txt`

Take a look at the output. Note that the _entire_ line containing five is returned and not just the string itself.

Wildcards and additional symbols can be used to make searches general or more specific. For instance, using

`grep fi* test.txt`

will match any string that starts with `fi`.

`grep ^five test.txt`

will only look for the string `five` if it is at the very beginning of a line.

`grep five$ test.txt`

will only look for the string `five` if it is at the end of a line.

There are many other possible patterns that can be used with `grep`. If you search online for grep cheat sheets, you can find a lot more information.

## Redirecting Output Streams

In the examples above, the output of the display commands (like `cat`, `head`, and `tail`) were all sent to the Terminal screen. However, there are many times when it is preferable to send this output to a file or even as the input to another command!

To send the output of any command to be stored in a file, you can use the redirection operators `>` and `>>`. These commands differ in whether they overwrite or append to a file. It's always safter to use `>>` if you're worried about losing the contents of an existing file. Note that if you overwrite a file's contents, there's __no__ way to get it back.

As one example, here's a way to send the contents of all text (`.txt`) files into a new text file called `allContents.txt`.

`cat *.txt >> allContents.txt`

You can also send the output of `head` or `tail` to a file in the same way

`head -n 20 test.txt >> testHeader.txt`

Sometimes the output of one command is also convenient to use as the input to another command. For instance, you could extract the first few lines of a file with `head` and then target the last few of these header lines with `tail`. To do this, we use a special type of redirection called piping. The pipe symbol is `|`. Here's one example of piping with `head` and `tail`:

`head -n 10 test.txt | tail -n 5`

Note that, in this case, `tail` does not need a filename as an argument. It is taking its input from the pipe.

As usual, this output is printed to the screen by default. But it can also be redirected to a file, even after piping:

`head -n 10 test.txt | tail -n 5 >> myLines.txt`

## Parsing File Contents

Another very powerful command is called `awk`, which can do lots of different forms of text parsing. For the purposes of this course, we will focus on using `awk` to extract individual columns (generally separated by spaces or tabs) from a file. The syntax we will use looks like this

`awk '{print $1}' test.txt`

This will print out the first column. To print the third column, we would use

`awk '{print $3}' test.txt`

To print both the first and third columns, we could do this

`awk '{print $1,$3}' test.txt`

## Deleting Files (CAREFUL!!)

Before you learn the next command, please note that __DELETING FILES AT THE COMMAND LINE CANNOT BE UNDONE__.

Since we can create files at the command line, we also need a way to delete them. However, deleting from the command line does not send a file to a trashcan from which we can go back and get them if we need. Command-line deletion is permanent, so proceed with caution.

To delete a file, you can use `rm`, which stands for "remove". Whenever possible, you should specify the precise file you want to delete, for instance

`rm test.txt` - delete `test.txt`

However, in some cases you may want to bulk delete all the files of a particular type. Again, wildcards are useful for this

`rm *.txt` - delete all text files

Be careful when using wildcards not to accidentally include unintended files.

The corresponding command to delete a folder is `rmdir`. For instance

`rmdir myFolder` - delete `myFolder`

Note that this command only works if a folder is empty. If there are files inside the folder, you can first delete these with `rm`, and then delete the folder with `rmdir`. You can also do these two steps in one, by specifying the recursive option (`-r`) to `rm`. Note that recursion will delete the folder and __anything__ nested inside it, including all files and other nested folders. Therefore, only use this if you're very confident it's want you want to do

`rm -r myFolder` - delete `myFolder` and everything nested inside it

Note that sloppy use of recursive deletion can cause you to delete entire sections of your filesystem!

> __Practice Exercise__
>
> (1) Use `history`, a pipe, `tail`, and `>>` to extract the last 50 lines from your command history and store them in a new file (`recentCommands.txt`).
>
> (2) Open your new file with `less` and scroll through to make sure the contents are correct.
>
> (3) Use `cp` to make another copy of this file (`recentCommands2.txt`).
>
> (4) Use `mv` to relocate the new copy to your Desktop folder (the precise path will vary depending on your system).
>
> (5) Change your working directory to your Desktop folder
>
> (6) Open `recentCommands2.txt` in `nano` and make some edits. Save your edits and quit `nano`.
>
> (7) Use `cat` to view the contents of your edited file and make sure it saved properly.
>
> (8) Use `rm recentCommands2.txt` to delete this new copy.

