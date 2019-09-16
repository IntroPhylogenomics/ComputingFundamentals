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

More information about options for the list command can be found [here](https://en.wikipedia.org/wiki/Ls). Adding the `-a` flag will display "hidden" files and folders

`ls -a` - list directory contents, including hidden files and folders

While these commands can indicate your location in the filesystem and the contents of that folder, you'll need to be able to change your location. This is accomplished with the change directory command

`cd <PATH_TO_NEW_LOCATION>` - change your working directory

Note that through these notes elements with angled branckets <...> should be replaced when executing commmands. For instance, if you are in a particular user's directory (e.g., `/Users/UserName/`) and you want to go to that user's desktop folder, you could use

`cd Desktop`.

In general, any relative or absolute path can be provided as an argument to `cd`. Remember also the special symbols like `..` and `~`. These are valuable shortcuts when moving around. For instance, to move to the parent of your current working directory, you can use

`cd ..`

Similarly, to move up two parents in the hierarchy, you could use

`cd ../..`

No matter where you are in your filesystem, you can immediately return to your home directory with

`cd ~`

and you can immediately get to the root with

`cd /`
