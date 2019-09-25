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

# Commenting

# Variables

# 
