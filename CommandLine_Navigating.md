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

`cd Desktop`

In general, any relative or absolute path can be provided as an argument to `cd`. Remember also the special symbols like `..` and `~`. These are valuable shortcuts when moving around. For instance, to move to the parent of your current working directory, you can use

`cd ..`

Similarly, to move up two parents in the hierarchy, you could use

`cd ../..`

No matter where you are in your filesystem, you can immediately return to your home directory with

`cd ~`

and you can immediately get to the root with

`cd /`

> __Practice Exercise__
>
> (1) Move to your home directory.
>
> (2) List your home directory contents
>
> (3) Move to a folder inside your home directory
>
> (4) Verify your current working directory
>
> (5) In one command, move to the _parent of your home directory_
>
> (6) Verify your current working directory

## Wildcards

One very powerful feature of working at the commandline is the ability to use wildcards. These are symbols that can match many other characters (or sets of characters) and allow you to list, view, or manipulate multiple files at once. The most general of these is `*`. This symbol can match any type or number of other characters. For instance, to list all of the files in a directory that end with `.txt`, you can use

`ls *.txt` - list all of the text files ending with `.txt`

You can also mix and match standard characters with wildcards for more sophisticated patterns. For instance, to find all the files that start with `m` and end with `.txt`, you can use

`ls m*.txt` - list all files starting with `m` and ending with `.txt`.

## Command History and Tab Completion

As you type in Terminal, it stores a record of the commands you've used recently. This feature can be very helpful if you need to reuse a command later. For instance, at a fresh command prompt, just press the up arrow key. You should now see the last command you used! If you keep pressing up, you can scroll back through your command history.

If you want to see this history, you can use the `history` command. 

`history` - display your latest command history

This will display all of your most recent commands on numbered lines.

Another useful trick when working at the command line is tab completion. As you start to type a command or a filename, the system will try and guess what you want if you press `tab`. If it is unable to distinguish among the possibilities, nothing will happen when you press `tab`. But if you've typed enough for the system to fill in the rest, it will!

For instance, type each of the following and see if the system can guess that you want to execute the `history` command.

`h` + `tab` - Does it autocomplete the command?

`hi` + `tab`

`his` + `tab`

`hist` + `tab`

`histo` + `tab`

`histor` + `tab`
