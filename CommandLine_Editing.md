# Editing Files and Folders from the Command Line

## Copying, Moving, and Renaming

You will often need to copy or rename a file from the command line. To copy a file inside your current working directory, you can use the copy command - `cp`. For instance, if you want to make a copy of a data file for a new analysis, you could use

`cp myData.txt myNewData.txt` - copy a file

You can also make copies that end up in other folders by adding a relative or absolute path before the filename

`cp myData.txt ../myNewData.txt` - copy data to the parent of current working directory

Moving and renaming files uses the same command - `mv`. If the source and destination filenames are in the same folder (e.g., the current working directory) then `mv` will simply rename the file

`mv myData.txt myOldData.txt` - rename myData.txt to myOldData.txt

However, if the source and destination filenames reference different folders, then `mv` will move the file

`mv myData.txt ..` - move myData.txt to parent of current working directory

You can also use `mv` to simultaneously move and rename a file

`mv myData.txt ../myOldData.txt` - both moves and renames myData.txt

## Creating New Files

## Viewing and Editing File Contents

## Deleting Files (CAREFUL!!)

Before you learn the next command, please note that __DELETING FILES AT THE COMMAND LINE CANNOT BE UNDONE__.
