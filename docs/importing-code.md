# Using Other People's Code
APL for a long time maintained and shared code and data in binary workspace files. In Dyalog, these are **.dws** files which are generated whenever you use the `⎕SAVE` system command.

Modern software practices, including the use of industry-standard source code managment tools, are predicated on the use of text files to store source code. Due to its history, Dyalog has several ways to import - and no standard dependency management system, although that is changing, as you can learn about in the section on [projects and packages]().

## Where to Find Code
Tools, interfaces and utilities are provided both by Dyalog pre-installed with standard installations, and also available in public repositories mainly on :fontawesome-brands-github: GitHub.

- the `)LIB` system command lists workspaces found in folders in the `[WSPATH]` configuration parameter
- the dfns workspace is primarily a pedagogical collection of utilities and experiments written in a functional style. Its contents are list on the dfns website

## The Get User Command
The experimental `]Get` user command is a one-stop shop utility for bringing code and data into the workspace. As a user command, it is a development time tool for convenience and should only be used in the interactive APL session. It covers common code and data formats, including

- binary workspaces
- link-compatible text source folders
- SALT-compatible text source files
- CSV files
- JSON files

and much more.

See `]Get -??` for more information.

## Link Import
Link can be used to import Dyalog APL functions, operators.

!!! Warning
    Tacit functions cannot be saved as text source. They must be wrapped in a Tradfn, Dfn or as part of a scripted class or namespace.

## Copy Workspace
Use `⎕CY` to copy part or whole of a **.dws** workspace file.

```apl
      'pmat'⎕CY'dfns'   ⍝ Permutations matrix
      pmat 2
1 2
2 1
```

An absolute or relative file path may be provided. Otherwise, directories in the `[WSPATH]` configuration parameter will be searched, followed by the current directory (`⊃1⎕NPARTS''`).

Workspaces in the `[WSPATH]` can be listed with the `)LIB` system command.
