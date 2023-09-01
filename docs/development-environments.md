# Development Environments
Dyalog's Integrated Development Environments allow you to interactively use APL to develop and debug applications.

<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video series: [Programming Environment Basics](https://www.youtube.com/playlist?list=PLA9gQgjzcpKEPltN7kEifZosjjVsFWVki)

On all platforms, Dyalog includes an Integrated Development Environment (IDE) to enable the interactive use of the APL notation to explore data, discover algorithms and create solutions. Using the IDE, the user can create an application through experimentation and easily diagnose problems, resolve issues and resume work. The IDE provides editors for functions and classes, and a tracer which allows the setting of break points, watch points, and full edit-and-resume capabilities.

Users can enhance the IDE through [User Commands](../application-development-and-deployment/user-commands.md). As part of the standard offering, Dyalog provides user commands that can, for example, interface to external source code management systems and search, replace and refactor code in the active workspace or in external code; you can further extend the IDE by implementing your own user commands.

## Dyalog IDE for Microsoft Windows
[:fontawesome-solid-file-pdf: Dyalog for Microsoft Windows UI Guide](https://docs.dyalog.com/latest/Dyalog%20for%20Microsoft%20Windows%20UI%20Guide.pdf)  
[:fontawesome-brands-dyalog: Introductory tutorial - Mastering Dyalog APL Chapter 2](https://mastering.dyalog.com/Getting-Started.html#the-standard-microsoft-windows-interpreter-working-environment)  

The [RIDE](#remote-ide-ride) is now the recommended IDE for macOS, AIX and Linux users. However, our native Microsoft Windows development environment remains the richest environment for the development of APL applications. Over the years, the Windows IDE has taken advantage of the Windows GUI to provide a Workspace Explorer, integrated search and replace tools, a language bar, tools for debugging GUI applications, an editor for nested arrays and integrated charting of data. Until the RIDE catches up, the classical Windows IDE is expected to remain the tool of choice for pure Windows development.

## Remote IDE (RIDE)
[:fontawesome-solid-file-pdf: RIDE User Guide](https://docs.dyalog.com/latest/RIDE%20User%20Guide.pdf)  
[:fontawesome-brands-dyalog: Introductory tutorial - Mastering Dyalog APL Chapter 2](https://mastering.dyalog.com/Getting-Started.html#the-ride-working-environment)  
[:fontawesome-brands-github: Dyalog/RIDE](http://github.com/Dyalog/ride)

The RIDE is a cross-platform, graphical development environment. It can run on macOS, Linux and Microsoft Windows, and can be used from any one of these platforms as a front end for Dyalog versions from 14.1 onwards.

The RIDE is available as a standalone application, or it can be accessed via a web browser by using the [configuration parameter](https://help.dyalog.com/latest/index.htm#UserGuide/Installation%20and%20Configuration/Configuration%20Parameters.htm) `RIDE_INIT=HTTP:<IP address>:<port>`. This is known as "zero-footprint" RIDE and is available out-of-the-box with installations of Dyalog on non-Windows platforms.

The standalone RIDE comes together with installations of Dyalog for macOS, but must be installed separately on Linux and Microsoft Windows.

The RIDE can be used to connect to remote interpreters over a network. The RIDE and connected Dyalog interpreters do not need to be running on the same device or platform.

## Terminal-based (TTY) IDE
[:fontawesome-solid-file-pdf: Dyalog for UNIX UI Guide - Driving the Dyalog APL tty version](https://docs.dyalog.com/latest/Dyalog%20for%20UNIX%20UI%20Guide.pdf#page=11)

The original interface to Dyalog is a UNIX (or VT-100) style terminal session. Despite only having a fixed-size screen full of characters, this interface does provide all of the interactive functionality mentioned in the introduction. We continue to provide this interface for use in situations where no GUI is available or where developers prefer the retro look!

## Using External Text Editors
:material-web: [Link User Guide](https://dyalog.github.io/link/)  
:fontawesome-brands-youtube: [Video: Link 3.0 // Morten Kromberg // Dyalog '21](https://dyalog.tv/Dyalog21/?v=K_-E1tnH06k)  

Link allows you to use Unicode text files to store APL source code, rather than "traditional" binary workspaces. The benefits of using Link and text files include:

- Changes to your code are immediately written to file: there is no need to remember to save your work. The assumption is that you will make the record permanent with a commit to your source code management system, when the time is right.
- Unlike binary workspaces, text source can be shared between different versions of APL - or even with human readers or writers who don't have APL installed at all.
- Source code stored in external files is preserved exactly as typed, rather than being reconstructed from the tokenised form.

## VSCode extensions
!!!Warning "These extensions are experimental"

<img style="width:5%; float:right;" src="https://code.visualstudio.com/assets/images/code-stable.png" />

[APL Language extension](https://marketplace.visualstudio.com/items?itemName=OptimaSystems.vscode-apl-language) adds APL syntax highlighting and snippets  

[APL Language Server Client extension](https://marketplace.visualstudio.com/items?itemName=OptimaSystems.vscode-apl-language-client) provides tool tips on primitives and a backtick [prefix keyboard input](../typing-apl/input-methods.md) method.

[VS Code APL Debug](https://github.com/tiamatica/vscode-apl-debug) allows stepping through APL code from VS Code

## Deploy with Docker containers
[:fontawesome-brands-youtube: Video: Dyalog's Docker Containers // Morten Kromberg // Dyalog '20](https://dyalog.tv/Dyalog20/?v=DeNkIYRehSs)  

Containers provide a consistent environment across different machines and operating systems. The effect is similar to that of virtual machines, but more lightweight and efficient.

<img style="width:15%; float:right;" src="https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png" />

With Docker containers you can:

- deploy easily to desktop, servers or in the cloud.
- package software and its dependencies in a standardised way.
- test your application in an environment similar to that in which it will be deployed.
- have your users obtain your software and its dependencies, ready to run, with a single command.
- deploy your application to the cloud and scale it easily with systems such as [kubernetes](https://kubernetes.io/) to meet demand as needed.

Read [the docker website](https://www.docker.com/resources/what-container/) to learn more about Docker containers and images.

Dyalog provides pre-made containers for:

- [The Dyalog Interpreter](https://hub.docker.com/r/dyalog/dyalog)
- [The Jarvis web service framework](https://hub.docker.com/r/dyalog/jarvis)
- [Dyalog Jupyter Notebooks](https://hub.docker.com/r/dyalog/jupyter)

Including support for interactive debugging using the [Remote IDE](https://docs.dyalog.com/latest/RIDE%20User%20Guide.pdf):

```shell
docker run -e RIDE_INIT=serve:*:4502 -p 4502:4502 dyalog/dyalog
```

Access from RIDE in a web browser:

```APL
docker run -e RIDE_INIT=http:*:8888 -p 8888:8888 dyalog/dyalog
```



### Error handling and debugging
<span class="logo-dyalog">:fontawesome-brands-dyalog:</span> Tutorial: [Mastering Dyalog APL Chapter 6 - First Aid Kit](https://mastering.dyalog.com/First-Aid-Kit.html)  
<span class="logo-dyalog">:fontawesome-brands-dyalog:</span> Tutorial: [Mastering Dyaloig APL Chapter M - Event Handling](https://www.dyalog.com/uploads/documents/MasteringDyalogAPL.pdf#page=539)  
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video series: [Error Handling in Dyalog](https://www.youtube.com/watch?v=tDK0AKXXRAk&list=PLA9gQgjzcpKF6UAG0EP0-8b1FM88k0GL_)  
<span class="icon-blog">:material-comment-text:</span> Blog post: [Enhanced Debugging with Function Keys](https://www.dyalog.com/blog/2018/09/enhanced-debugging-with-function-keys/)  

The basic method of debugging is to trace through a function using **Action → Trace** or typing <kbd>Ctrl+Enter</kbd> with the text cursor on the expression you want to trace through. You can then step through multi-line functions one expression at a time.

Learn how to interpret error messages, trace the execution of an application step-by-step, and set break points to help debugging in the [First-Aid Kit chapter of Mastering Dyalog APL](https://mastering.dyalog.com/First-Aid-Kit.html).


