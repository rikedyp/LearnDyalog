# Asynchronous Programming
This page shows constructs which can be used to explicitly manage asynchronous, concurrent execution of code.

More detailed discussion about the potential for automatic parallelisation and the use of explicit parallelisation is given in the document on [parallel language features](https://docs.dyalog.com/latest/Parallel%20Language%20Features.pdf).

## The Spawn Operator
[:material-web: Mastering Dyalog APL section 11.12](https://mastering.dyalog.com/Operators.html?highlight=spawn%20operator#spawn)  
[:material-web: Spawn documentation](http://help.dyalog.com/latest/#Language/Primitive%20Operators/Spawn.htm)  

The Spawn operator `&` is a lightweight method for doing multiple time-consuming (but not compute-heavy) tasks in parallel. Examples of tasks which may benefit from this type of parallel execution include web scraping and database operations.

## Futures and Isolates
[:fontawesome-brands-dyalog: Blog post: Isolated Mandelbrot Set Explorer](https://www.dyalog.com/blog/2014/08/isolated-mandelbrot-set-explorer/)  
[:fontawesome-solid-file-pdf: Parallel Language Features](https://docs.dyalog.com/latest/Parallel%20Language%20Features.pdf)  

Futures and isolates are a mechanism for executing functions in parallel, allowing a program to take advantage of multiple cores or processors. The developer can declare which parts of an application should be run in separate CPU threads.

Examples of tasks which may benefit from this type of multi-core parallel execution include data processing, financial calculations and scientific simulations. Tasks will benefit when the compute time for running sub-tasks is greater than the time to set up new isolates and transfer data between them.

An isolate is a [namespace](https://course.dyalog.com/Namespaces/) within which all execution is asynchronous relative to the main programme. Any reference to a function or variable within an isolate immediately returns a future, a special type of value which can be passed around as an argument or an element of an array while the calculation is ongoing. Execution of the main programme will automatically block until the asynchronous call completes if an expressions is encountered which requires the actual value, if the asynchronous computation has not completed.

## .NET Tasks
The [.NET Task Class](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task?view=net-6.0) can be used directly from Dyalog APL using the [.NET interface](./external-language-interfaces-standard-libraries.md#net).

## Experimental Features
[:material-web: 2022 Conference Edition README](https://www.dyalog.com/uploads/dyalog_readme_120.22.htm)  
[:fontawesome-brands-youtube: 2022 Conference Edition Part 3a - Future(s) // John Daintree // Dyalog '22](https://dyalog.tv/Dyalog22/?v=P18Z3ilH378)  
[:fontawesome-brands-youtube: 2022 Conference Edition Part 3b - Future(s) // John Daintree // Dyalog '22'](https://dyalog.tv/Dyalog22/?v=nkqds8YavmQ)  

The 2022 Conference Edition of the Dyalog interpreter includes experimental functionality, including a unifying interface for managing the asynchronous running of functions using any of the available mechanisms.
