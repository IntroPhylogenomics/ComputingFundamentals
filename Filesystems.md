# Filesystems

## Filesystem Structure

The base of the filesystem in Unix-based operating systems (like Linux and Mac OS, which we will focus on exclusively in this workshop) is indicated with a single forward slash (`/`) and is known as the filesystem's root. The location of all files and folders can be written with a __path (i.e., address) that starts at the root__. Folders are hierarchical, so paths to highly nested folders will need to include all parent folders.
  
![ExampleMacFilesystem](https://github.com/IntroPhylogenomics/ComputingFundamentals/blob/master/exampleFilesystem.png)
  
For instance, in the example above, the location of the `Users` folder can be written as `/Users/`, the location of the home directory for `UserName` can be be written as `/Users/UserName/`, and the location of their desktop folder can be written as `/Users/UserName/Desktop/`.
  
## Absolute v Relative Paths
  
While the addresses for all files and folders can be written with paths that start at the root, it's sometimes cumbersome to do so. For instance, if you want to reference the parent folder of the folder you're in, it would be easier to provide the address that way (i.e., the parent of the folder I'm in), rather than write out the full path from the root. Paths that provide locations this way are known as __relative paths__. These are in contrast to __absolute paths__ that always start at the root, `/`. Relative paths simply indicate where to look based on where you are. For instance, if your working directory is already `/Users/UserName/`, then you can reference the user's desktop folder by just writing `Desktop`. There are special symbols used to indicate the folder you're in (i.e., the current working directory) - `.` - and the parent folder of the current working directory - `..`. Another commonly used special symbol is `~`, which indicates the home directory of the user.


> __Practice Exercise__
>
> If your current working directory is `/Users/UserName/`, write the absolute paths for the 
> directories referenced by the following relative paths.
>
> `Desktop`
>
> `../Guest/`
>
> `~/Library/`
>
> `../../`
  
## Hidden Files and Folders

In Unix-based filesystems, you can keep some files and folders from showing up by default if you add a period, `.`, to the beginning of their names. These files are hidden. One common use for hidden files is to specify configuration settings for a program or system. These hidden files are usually stored in a user's home directory (e.g., `/Users/UserName/`). They can be revealed by listing a directory's contents using the `-a` flag - `ls -a`.

## The PATH Variable

Whenever you type a command in Terminal, the shell needs to know where to locate the program that tells it how to execute that command. As it turns out, every Terminal command is its own program! To find the relevant programs, the shell uses a special variable called `PATH`. In `PATH`, the shell stores a list of paths that it examines (in order) to look for any command you type. You can see this list of paths by typing

`echo $PATH` - (we'll look into how this works later)

When you type this command, you should see a list of absolute paths separated by `:`s. The directories where your typical Unix commands are stored have paths like `/bin`, `usr/bin`, and `usr/local/bin`.

If you install new command-line software and want to be able to run it just by typing its name, the shell needs to be able to find it using `PATH`. You can make this possible in one of two ways:

- (1) You can move a copy of the software to one of the folders already found in `PATH`
- (2) You can add the folder where your software is located to `PATH`.

To add a new folder to `PATH`, you can use a command like this

`PATH=$PATH":/path/to/my/folder"`
