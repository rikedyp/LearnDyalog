# Development-time Tools

## Projects and Packages
Due to the terse and malleable nature of APL, copying and modifying source code for use in a specific project has been favoured over the use of ready-made black-box "packages". Furthermore, many APL users developed their own in-house source code and project management systems.

Recently there have been some efforts made to develop general project and package managers for Dyalog APL.

### Cider & Tatin
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [Dado (Dyalog Development Operations) // Josh David // Dyalog '21](https://dyalog.tv/Dyalog21/?v=AFvfBE19OFg).

<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [The P words…Projects and Packages](https://dyalog.tv/Dyalog21/?v=AFvfBE19OFg) // Morten Kromberg // Dyalog '22.

<img src="../img/tatin.ico" width="16px" alt="Tatin logo icon" /> [Tatin](https://tatin.dev/) is a package manager for Dyalog APL. You can publish APL projects to the Tatin registry for others to use. It is currently under heavy development but there are already packages available to use. It is a convenient way to import useful libraries written in APL, and offers robust dependency management system.

:fontawesome-brands-github: [Cider](https://github.com/aplteam/Cider) is a project manager for Dyalog APL. It provides a framework for organising APL projects and their dependencies, and gives a simple workflow for opening projects for development in Dyalog.

### Dado
Dado combines the functionality of Cider and Tatin, and has tight integration with GitHub.

The key functionalities of this DevOps system for Dyalog include:

- streamlined cover functions for git commands
- "one-click" releases to automatically generate release notes, handle application versioning, and upload assets
- dependency management
- a built-in git workflow

This can all be done with a few simple user command functions, without having to leave the Dyalog session.

## User Commands

