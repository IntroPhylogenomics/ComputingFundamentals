# Practical Computing Tips

## Naming files and folders

Developing good habits (and breaking bad ones) for naming files and folders will make your life much easier in the long run. Many computing errors result from code just having trouble reading names properly. The most important rule is to __NEVER use spaces!__ Doing so will frequently cause programs to only read part of the name. Also, it's a good idea to avoid special characters (like $, \*, @, etc.) whenever possible. Some widely used approaches to filename syntax are:

- CamelCaseLooksLikeThis
- underscores_can_work

Find a style that you like and stick with it. Consistency helps a lot.

## Plain text files
	
Nearly all files that you'll use for storing data and results in phylogenomics or bioinformatics are plain text files. These files may have special names (like Nexus files - .nex), but these names just mean that these text files have been formatted according to a particular set of requirements. They can all be opened by a text editor and are human readable. Text files store characters using widely accepted standards like ASCII and UniCode.

- [ASCII on Wikipedia](https://en.wikipedia.org/wiki/ASCII)
- [UTF-8 on Wikipedia](https://en.wikipedia.org/wiki/UTF-8)

Note that more specialized and proprietary file types (like .jpg, .pdf, .docx) are not plain text and, therefore, are not human readable.

## Text Editors

The first step in getting set up for any computing project is to download a good plain text editor. Note that __word processing programs (like Microsoft Word) are not plain text editors__ and cannot be used for file editing. A number of very good plain text editors are readily available. For Macs, try [BBEdit](https://www.barebones.com/products/bbedit/). An excellent editor available for all major platforms (Mac OS, Linux, and Windows) is [Sublime](https://www.sublimetext.com/3). 

## Newline characters
	
One frequent cause of errors (and headaches) for those who move between different operating systems (especially with Windows) has to do with the type of character used to indicate the end of a line (called a "newline character"). These characters differ between operating systems, so a text file generated on a Linux system may not be read properly on Windows (and vice versa). Thankfully, good text editors make it easy to check and change the type of newline characters used in a file. For instance, BBEdit has a drop down menu at the bottom of every file that allows you to choose between "Legacy Mac (CR)", "Unix (LF)", and "Windows (CRLF)".
	
- [New Lines on Wikipedia](https://en.wikipedia.org/wiki/Newline)

## Activity Monitor

As you start running analyses, you will frequently want to keep track of what's running on your computer and what kind of resources (e.g., processor time, memory) each task is using. To do this, most operating systems come with some kind of built-in activity monitor. For instance, on Mac OS, you can find the Activity Monitor program in Applications > Utilities. These programs should provide information about the tasks that are running, their ID numbers, and their usage of CPU, memory, and disk space. We will talk about how to use this information to manage tasks later in the workshop. At the command line on any Unix-based system, you should be able to find similar information with the command `top`, and sometimes `htop`.
