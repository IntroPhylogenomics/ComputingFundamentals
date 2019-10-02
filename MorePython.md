# More With Python

## If Statements

If statements in Python are similar in form to Bash, but simpler. The general form is

```
if <CONDITION>:
    <DO_THIS>
```

The `if` statement has to finish with a `:`. Also, in Python, the code block inside the `if` statement __must__ be indented. You can use either tabs or a certain number of spaces. When using spaces, you must use the __same__ number of spaces throughout your code. The official recommendations for Python style strongly suggest using 4 spaces, rather than tabs.

The syntax for logical tests is quite intuitive in Python. To test equality, use two equals signs, `==`.

`myStr == "some text"`

You can test if two things are _not_ equal with `!=`.

`myStr != "other text"`

`if` statements can be used on their own, but no code will be executed when the condition is false.

## If...Else Statements

To include code blocks that should be executed when the condition is false, you'll need to use an `if...else` statement. These have the general form:

```
if <CONDITION>:
    <DO_THING_WHEN_TRUE>
else:
    <DO_THING_WHEN_FALSE>
```
            
Sometimes, you'll want to test a series of conditions to decide what to do. In that case you could use a nested set of `if...else` statements:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
else:
    if nuc == "C":
        print("Nucleotide is a C.")
    else:
        if nuc == "G":
            print("Nucleotide is a G.")
        else:
            if nuc == "T":
                print("Nucleotide is a T.")
```      

However, you'll notice that this can get pretty cumbersome pretty quickly. Thankfully, python offers another, more compact, way to write this:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T"
    print("Nucleotide is a T.")
```
            
The `elif` statements stand for `else...if` and capture what we tried to do above with the nesting.

It is important to realize that as we've currently written these statements, nothing would happen if the variable `nuc` didn't have the value `A`, `C`, `G`, or `T`. This can be a big problem when accepting input from a user or file that might provide an unintended value. To capture these cases, it's always best to close with a simple `else`:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T":
    print("Nucleotide is a T.")
else:
    print("This is not a valid nucleotide!")
```
