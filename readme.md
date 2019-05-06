# Infix incremental addition

I was looking for an equivalent to the += python operator in R; firstly out of curiosity and then to just not be beaten by something so simple.

In R, infix operators (operators sandwiched with %, ie, %.%) take arguments on the left and right sides to be closer to standard arithmetic functions. Using the infix structure, I created a simple compounded arithmetic operator for addition:

```
`%+%` < - function(x, y) {
    eval.parent(substitute(x <- x + y))
}
```

The trick is to call eval.parent to evaluate the function in the environment above it, not the function environment. This type of operator is especially handy in a loop created by a generator function, like looping through files in a directory. We’ll test out our operator:

```
 x <- 1
for (i in 1:10) {
    x %+% 1
}
x
[1] 56
```
This exercise may be superfluous but definitely cuts down on verbosity during loops.

