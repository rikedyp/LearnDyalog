# Getting started with Dyalog APL
You do not need to install anything to get started using and learning the APL language.

You can get started with the materials listed here using the [TryAPL online interpreter](https://tryapl.org). 

## Quick Start
If you do decide to install Dyalog, the following instructions should get you up and running with a standard workflow.

### Installing Dyalog
You can [download Dyalog for free](https://www.dyalog.com/download-zone.htm) from the Dyalog website. Also see the [installation instructions for the latest version of Dyalog on all platforms](https://docs.dyalog.com/latest/setup_readme.htm).

### Interactive REPL

*[REPL]: Read Evaluate Print Loop - enter expressions and see their results

<span class="logo-youtube">:fontawesome-brands-youtube:</span> [Editing and Debugging Dyalog APL](https://youtu.be/0CYReeNue6A).

When you start Dyalog, you are met with a blank area with a text cursor. This is the session window. You can input APL expressions (usually indented by 6 spaces) and press enter to see their results:

```APL
      1+2
3
```

To create a function you can use: the `⎕ED` system command; double click on a name; or press <kbd>Shift+Enter</kbd> with the cursor on a name.

```APL
⎕ED'MyFunction'
```

You can now write a tradfn or dfn ([APL Course: User-defined Functions](https://course.dyalog.com/user-defined-functions)) in the editor.

Pressing <kbd>Esc</kbd> will close the editor and save your changes in the active workspace. The active workspace is the currently running set of code - functions and variables etc.

### Save your work

Create a link between the active workspace and a folder on the file system:

```APL
      ]Create # /tmp/MyProject
Linked: # ←→ C:\tmp\MyProject [directory was created]
```

Now, when you make a change using the editor (after closing it with <kbd>Esc</kbd>), a file in that folder will be created or updated.

For larger applications or complex workflows, you might want to learn about [projects and packages](./application-development/projects-and-packages.md).

### Quit Dyalog
Use `)OFF` to exit Dyalog

!!!Note "Your session log"
	Your session log will be saved in the location specified by the `LOG_FILE` [configuration parameter](https://course.dyalog.com/Interpreter-internals/#configuration-parameters).

	```
	]Config LOG_FILE
	```

## Tips
Check out our [page of tips](./getting-started/tips.md) suggested by users.
