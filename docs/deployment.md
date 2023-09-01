# Deploying Dyalog APL Applications
Once you have written some code to solve your problem, you might want to make it available for others to use. Your users may be other specialists in your field, or other people looking to do similar processing or analysis as you. They may or may not also be APL users.

## Delivering Your APLs
See [materials for the talk "Delivering Your APLs"](https://github.com/mkromberg/deliverapl), which demonstrates deploying an APL application as:

- an interactive APL application
- a standalone GUI application for Microsoft Windows
- a \#! (shebang) script using dyalogscript
- a cross-platform HTML-based GUI application
- integration with Python using Py'n'APL
- a shared library callable from most languages with a foreign function interface
- a web service in a docker container
- a .NET assembly generated from APL code

## APL Packages
Development operations are not standardised in the APL community, but have been developed by various organisations for their own purposes. Some work has gone into making tools available for the community.
[The P words…Projects and Packages // Morten Kromberg // Dyalog '22](https://dyalog.tv/Dyalog22/?v=3dljAUEvemE)

## Providing Web Services
Modern applications commonly expose functionality as services which accept requests using HTTP.

[Jarvis](https://dyalog.github.io/Jarvis/) is a tool which allows users to easily expose APL functions as a web service. In JSON mode, endpoints have the same name as APL functions and JSON payloads are converted to APL arrays and passed to the function as argument. In REST mode, you can specify which HTTP methods to support (or even create your own) and requests are passed, including the endpoint and any query parameters, to a function 

[Simplifying Secure, Scalable Web Services // Brian Becker // Dyalog '22 ](https://www.youtube.com/watch?v=RJHnUFHd4ak)

- check webinars
- check workshops
- link to APL as a Shared Library
- mention PynAPL I guess (deliverapls summary)

- standalone exe [StackOverflow question](https://stackoverflow.com/questions/60698569/dyalog-apl-how-to-write-standalone-files-that-can-be-executed)
- DyalogScript