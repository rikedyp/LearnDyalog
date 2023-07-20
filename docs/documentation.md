# Using the Dyalog Documentation
Dyalog has documentation in several sources. This page gives an overview and tips on navigating and interpreting our documentation.

All documentation is linked from the [Documentation Centre](https://docs.dyalog.com).

A subset of the documentation pertaining to the APL language, IDE for Microsoft Windows and some other tools is available

> Hint: Press <kbd>F1</kbd> with your cursor ⌶ on a glyph to open the documentation.

Functions, for example [subtract (`X-Y`)](https://help.dyalog.com/latest/#Language/Primitive%20Functions/Subtract.htm), have a key which describes their syntax:
```
{R} ← {x} F Y
```

The syntax reflects that of a [traditional function header](https://course.dyalog.com/user-defined-functions/#traditional-functions).

For a function `F`: `R` is the result, `X` is the left argument and `Y` is the right argument.

Results in `{}` curly braces are called **shy results** and do not print to the session by default, but can be passed to arguments.

If the left argument `X` is in curly braces, then it is **optional**.
