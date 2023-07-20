# Application Development and Deployment

## Development environment
- <span class="logo-youtube">:fontawesome-brands-youtube:</span> Video series: [Programming Environment Basics](https://www.youtube.com/playlist?list=PLA9gQgjzcpKEPltN7kEifZosjjVsFWVki)
- Link
	- [Link User Guide](https://dyalog.github.io/link/)
	- Video: [Link 3.0 // Morten Kromberg // Dyalog '21](https://dyalog.tv/Dyalog21/?v=K_-E1tnH06k)
- WIDE
- RIDE
- TTY
- External editors
- User commands

## Projects and Packages
Due to the terse and malleable nature of APL, copying and modifying source code for use in a specific project has been favoured over the use of ready-made black-box "packages". Furthermore, many APL users developed their own in-house source code and project management systems.

Recently there have been some efforts made to develop general project and package managers for Dyalog APL.

### Cider & Tatin
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [The P words…Projects and Packages](https://dyalog.tv/Dyalog21/?v=AFvfBE19OFg) // Morten Kromberg // Dyalog '22.

<img src="../img/tatin.ico" width="16px" alt="Tatin logo icon" /> [Tatin](https://tatin.dev/) is a package manager for Dyalog APL. You can publish APL projects to the Tatin registry for others to use.

:fontawesome-brands-github: [Cider](https://github.com/aplteam/Cider) is a project manager for Dyalog APL. It provides a framework for organising APL projects and their dependencies, and gives a simple workflow for opening a project in the session.

### Dado
Dado combines the functionality of Cider and Tatin, and has tight integration with GitHub.

The key functionalities of this DevOps system for Dyalog include:

- streamlined cover functions for git commands
- "one-click" releases to automatically generate release notes, handle application versioning, and upload assets
- dependency management
- a built-in git workflow

This can all be done with a few simple user command functions, without having to leave the Dyalog session.

<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [Dado (Dyalog Development Operations) // Josh David // Dyalog '21](https://dyalog.tv/Dyalog21/?v=AFvfBE19OFg).

## Application deployment
- [DeliverAPL](https://github.com/mkromberg/deliverapl)
- workspaces
- Tatin packages
- standalone exe [StackOverflow question](https://stackoverflow.com/questions/60698569/dyalog-apl-how-to-write-standalone-files-that-can-be-executed)
- DyalogScript

## Error handling and debugging
<span class="logo-dyalog">:fontawesome-brands-dyalog:</span> Tutorial: [Mastering Dyalog APL Chapter 6 - First Aid Kit](https://mastering.dyalog.com/First-Aid-Kit.html)  
<span class="logo-dyalog">:fontawesome-brands-dyalog:</span> Tutorial: [Mastering Dyaloig APL Chapter M - Event Handling](https://www.dyalog.com/uploads/documents/MasteringDyalogAPL.pdf#page=539)  
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video series: [Error Handling in Dyalog](https://www.youtube.com/watch?v=tDK0AKXXRAk&list=PLA9gQgjzcpKF6UAG0EP0-8b1FM88k0GL_)  
<span class="icon-blog">:material-comment-text:</span> Blog post: [Enhanced Debugging with Function Keys](https://www.dyalog.com/blog/2018/09/enhanced-debugging-with-function-keys/)  

The basic method of debugging is to trace through a function using **Action → Trace** or typing <kbd>Ctrl+Enter</kbd> with the text cursor on the expression you want to trace through. You can then step through multi-line functions one expression at a time.

Learn how to interpret error messages, trace the execution of an application step-by-step, and set break points to help debugging in the [First-Aid Kit chapter of Mastering Dyalog APL](https://mastering.dyalog.com/First-Aid-Kit.html).


