# Math in Bash

In general, bash isn't very good for mathematical operations, but it can be done in several ways. Probably the easiest is to wrap a mathematical expression in _double_ parentheses and precede it with a `$`, since you pretty much always want the _value_ of the mathematical result.

- `echo $(( 2 + 2 ))`
  - `myNum = $(( 2 + 2 ))`
- `echo $(( 3 * 6 ))`
- `echo $(( 20 / 3 ))`
- `echo $(( 20 % 3 ))`

> Compare the output of these last two lines? What's going on?

NOTE: bash can only handle _integers_ and not floating-point numbers (i.e., decimals)

Try this. What happens?

    - `myVar=3`
    - `echo $myVar`
    - `((myVar++))`
    - `echo $myVar`
    - `((myVar++))`
    - `echo $myVar`

What does the `++` operator do?
