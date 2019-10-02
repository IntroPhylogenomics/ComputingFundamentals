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
