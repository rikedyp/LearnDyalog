*Cider & Tatin*

It is useful to clarify that Tatin is to serve as both a PDM (project/application dependency manager) and an LPM (language package manager) - using language from the article [So you want to write a package manager](https://medium.com/@sdboyer/so-you-want-to-write-a-package-manager-4ae9c17d9527) which Stefan sent - and indeed eventually one of the main places users look to find ready-to-use code to include in their development environments and projects. This must be the case because we are spending so much time considering the installation of user commands, which would generally not be a dependency of a project for the sake of the user command. 

## Terminology
|Term|Definition|
|---|---|
|Registry|An index of packages and location from which they may be installed|
|Installation folder|A folder with a dependencies list, build file and packages|
|StartupSession|Whatever code is loaded into `⎕SE` at Dyalog startup|
|To install a package|To take a package from a registry to an installation folder|

## Loading a subset of packages from an installation folder
We are considering adding a way to load a subset of packages from an installation folder into the active workspace. This addresses two use cases:
1. packages which come pre-installed with Dyalog can be placed in a single folder and a subset can be marked for loading into `⎕SE` at startup
2. users can use installation folders as a way to specify a set of packages available in different environments (but not always all loaded into the workspace in such enviroments)

It is still a (future) requirement that there be a mechanism to copy packages between registries. This still raises the question of what is the difference between a registry and an installation folder. Gil mentioned that at a basic level a registry can be a folder with packages in it which the Tatin client manages - it is only when you want multiple users to manage a registry that you require a server.

## User commands
Currently the user command system scans all folders on the `cmddir` path recursively looking for namespace scripts which look like user commands.

We could change UCMD framework to have API to add specific UCMD scripts, then Dyalog can call Tatin.Run and Tatin could call "UCMD.Add *list of scripts*"
`Tatin.Install -enableucmd -ucmd=on/off`
`Tatin.UCMD APLGit2 -enable/disable -on/off`
`Tatin.Uninstall` 

## Tatin functions to do this stuff

### Add
`Tatin.Add`
Add a package as a dependency of a project. It may be that [install](#install) does this on the Tatin side, while Cider has `Add` because it is explicitly adding dependencies.

### Install
- copy a package and meta data from a registry to an installation folder
	- add a reference to a package to a dependencies list
	- add details of registry and version to a build list (aka manifest)
	- add files to a sub folder

### Load
Bring one or more packages' code and assets from a registry into the system temporary folder, bring that code into the active workspace and establish references in the target namespace (default `⎕THIS`)

### Import
Bring a subset of packages from an installation folder into the active workspace - establish references in the target namespace (default `⎕THIS`)

### LoadDependencies
Alias for [importing](#import) all packages from an installation folder into the active workspace

### Copy
Copy a package (fully qualified version) from a source registry to a target registry
