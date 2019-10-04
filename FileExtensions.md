# Changing File Extensions

Let's say you have a whole series of files that end with the extension `.txt`
and you'd like to rename them to have `.text` extensions. But, you don't know
how many `.txt` files you might have or what their names will be. Thankfully,
this is where wildcards become incredibly helpful. Remember that the bash shell uses 
a single `*` as its most general wildcard. So, typing `*.txt` will automatically give 
you all the filenames that end with `.txt`.

Note that there's a special command called basename that strips off whatever text 
you want from the end of a string. So, typing

`basename test.txt .txt`

will give you just `test` in return.

See if you can create a script that uses a `for` loop to go through all
of the `.txt` files in a folder and give them the extension of `.text`.
