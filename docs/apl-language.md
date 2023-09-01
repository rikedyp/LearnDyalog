# APL Language
APL language is a very ergonomic language for problem solving. Once you have learned the basic syntax and some of the functionality, it is likely you will be able to tackle a wide range of problems and come to a working solution. That may not be the *optimal* solution, in terms of readability, maintainability or computational efficiency - but it is hopefully a *correct* solution.

### Language tutorials and examples

### Problem Solving with APL
- problems.tryapl
- kattis
- problem solving competition
- advent of code
- rosalind.info
- rosetta code

## Asynchronous Programming
This page shows constructs which can be used to explicitly manage asynchronous, concurrent execution of code.

More detailed discussion about the potential for automatic parallelisation and the use of explicit parallelisation is given in the document on [parallel language features](https://docs.dyalog.com/latest/Parallel%20Language%20Features.pdf).

### The Spawn Operator
[:material-web: Mastering Dyalog APL section 11.12](https://mastering.dyalog.com/Operators.html?highlight=spawn%20operator#spawn)  
[:material-web: Spawn documentation](http://help.dyalog.com/latest/#Language/Primitive%20Operators/Spawn.htm)  

The Spawn operator `&` is a lightweight method for doing multiple time-consuming (but not compute-heavy) tasks in parallel. Examples of tasks which may benefit from this type of parallel execution include web scraping and database operations.

### Futures and Isolates
[:fontawesome-brands-dyalog: Blog post: Isolated Mandelbrot Set Explorer](https://www.dyalog.com/blog/2014/08/isolated-mandelbrot-set-explorer/)  
[:fontawesome-solid-file-pdf: Parallel Language Features](https://docs.dyalog.com/latest/Parallel%20Language%20Features.pdf)  

Futures and isolates are a mechanism for executing functions in parallel, allowing a program to take advantage of multiple cores or processors. The developer can declare which parts of an application should be run in separate CPU threads.

Examples of tasks which may benefit from this type of multi-core parallel execution include data processing, financial calculations and scientific simulations. Tasks will benefit when the compute time for running sub-tasks is greater than the time to set up new isolates and transfer data between them.

An isolate is a [namespace](https://course.dyalog.com/Namespaces/) within which all execution is asynchronous relative to the main programme. Any reference to a function or variable within an isolate immediately returns a future, a special type of value which can be passed around as an argument or an element of an array while the calculation is ongoing. Execution of the main programme will automatically block until the asynchronous call completes if an expressions is encountered which requires the actual value, if the asynchronous computation has not completed.

### .NET Tasks
The [.NET Task Class](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task?view=net-6.0) can be used directly from Dyalog APL using the [.NET interface](./external-language-interfaces-standard-libraries.md#net).

### Experimental Features
[:material-web: 2022 Conference Edition README](https://www.dyalog.com/uploads/dyalog_readme_120.22.htm)  
[:fontawesome-brands-youtube: 2022 Conference Edition Part 3a - Future(s) // John Daintree // Dyalog '22](https://dyalog.tv/Dyalog22/?v=P18Z3ilH378)  
[:fontawesome-brands-youtube: 2022 Conference Edition Part 3b - Future(s) // John Daintree // Dyalog '22'](https://dyalog.tv/Dyalog22/?v=nkqds8YavmQ)  

The 2022 Conference Edition of the Dyalog interpreter includes experimental functionality, including a unifying interface for managing the asynchronous running of functions using any of the available mechanisms.


!!!Example "Online coding challenge: the weekly APL Quest"
	Come to the [APL Orchard](https://apl.chat) every Friday. For more information including how to join, see the [APL wiki article about APL Quest](https://aplwiki.com/wiki/APL_Quest).

	[<span class="logo-youtube">:fontawesome-brands-youtube:</span> Videos from Adám Brudzewsky](https://youtube.com/playlist?list=PLYKQVqyrAEj9wDIUyLDGtDAFTKY38BUMN) summarise solutions to APL Quest problems.

## Examples

- student competition
- rosetta code
- rosalind
- Kattis
- problems.tryapl.org
- youtube shorts

### [Notebook: Justifying Text](https://github.com/Dyalog/dyalog-jupyter-notebooks/blob/master/Justifying%20Text.ipynb)
This notebook takes a look at how to write some _array-oriented_ APL code that justifies some text. In case you are wondering what "justified text" is, take a look at the [example in the Wikipedia](https://en.wikipedia.org/wiki/Typographic_alignment#Examples).

(The content of this notebook draws heavily from [Lesson 42](https://chat.stackexchange.com/rooms/52405/conversation/lesson-42-array-coding-style-in-depth) of the [APL Cultivation chat lessons](https://chat.stackexchange.com/rooms/info/52405/the-apl-orchard?tab=conversations) and is a written follow-up to Rodrigo Girão Serrão's presentation at [APL Seeds'21](https://www.dyalog.com/apl-seeds-user-meetings/aplseeds21.htm).)

### [Notebook: Boolean Scans and Reductions](https://github.com/Dyalog/dyalog-jupyter-notebooks/blob/master/Boolean%20Scans%20and%20Reductions.ipynb)
These techniques for manipulation of Boolean arrays are general purpose and useful when writing high performance code. 

## Language design and development
[<span class="icon-blog">:material-comment-text:</span> Blog posts about APL language design](https://www.dyalog.com/blog/tag/language-design/).

### Paradigms
- Array oriented
- Functional programming
- Object-oriented programming
- Asynchronous programming
	- [Mandelbrot set blog post](https://www.dyalog.com/blog/2014/08/isolated-mandelbrot-set-explorer/)

### Language concept tutorials
- Boolean Scans and Reductions
- Arithmetic + other Jupyter notebooks
