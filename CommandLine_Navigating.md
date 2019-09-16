# Navigating at the Command Line

## Terminal

The filesystem on Unix-based systems can be accessed not only through the point-and-click graphical user interfaces (GUIs) that we're all used to, but also by typing text commands. These commands are entered through an interface called the Terminal. On Mac OS X, Terminal can be found in `Applications > Utilities`. After opening Terminal, you can type commands at the command prompt (which usually ends with `>` or `$`).

## Commands for Navigating

To start navigating the filesystem, it helps to know where you are (i.e., your current working directory). You can print the absolute path to your current location using

`pwd` - print working directory.

After opening Terminal, use `pwd` to see the default working directory. To view the contents of this (or any) folder, you can use the list command

`ls` - list the contents of a directory.

To see more information about these contents you can add the `-l` flag (i.e., option) to the list command

`ls -l` - list directory contents in the long format.

More information about options for the list command can be found [here](https://en.wikipedia.org/wiki/Ls).
