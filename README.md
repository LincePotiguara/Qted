The 4coder code base was authored by Allen Webster from 2014-2022, with help from a number of contributors:
+ Casey Muratori
+ "insofaras" Alex Baines
+ Yuval Dolev
+ Ryan Fleury

Allen thanks to all those who supported the project, financially and/or through all your detailed feedback.

As of May 31st 2022, the codebase was archived and open sourced.

This fork is intended to provide bug fixes and restructuring some systems.

# Build Instructions


1. Clone the companion repository and the "4coder-non-source" repository
```shell
git clone https://github.com/Dion-Systems/4coder-non-source.git
```
2. Run `mkdir 4ed` to create an empty folder named "4ed" to contain the codebase
3. Navigate to the folder `cd 4ed`
4. Clone this project 
```shell
git clone https://github.com/LincePotiguara/Qted.git
```
5. Run `rename Qted code` to rename the folder containing the repository to "code"
6. Setup the visual studio command line environment variables
* On windows setup the visual studio command line, the script is something like this
```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"
```
* On linux setup g++
7. Navigate to the "4ed/code" folder `cd code`
8. Run the build script that builds the metaprogram that builds the program. This system needs restructuring
* On windows run `bin\build.bat`
* On linux run `bin\build-linux.sh`
* Mac is not supported currently
9. Create a folder `mkdir fonts` inside executable folder and put a font file there. The default font is `liberation-mono.ttf`


# Notes on Major Issues

1. The build system and organization of files is extremely complicated. There is a 4ed_build.cpp that defines how builds run, and the build scripts have to build and run this C++ file. The file is pretty chaotic since it cannot rely on the codebase's usual helpers. On top of that there is a totally separate build system for the custom layer which is also a big gigantic mess of its own. It involves several stages of compilation, and a number of metaprograms.

2. The documentation system is over complicated & the documentation is incomplete. There is very little documentation for the internals or the complicated layers of helpers.

3. The lexer generator is way too complicated, and the built-in support for language features is not fully developed. The background threaded parsing is not very carefully organized and is not very flexible, so it's hard to add new languages at any level of the system.

4. There are a few layers of overcomplicated configuration parsers.

5. Mac support has not been maintained for several versions.

6. The codebase has a very weak base layer with key features that were added very late, so lots of code was written in the absence of useful features to bind things together. To make matters worse the base layer is split by the distinction of custom layer & core layer, leading to some double definitions and some incosistencies.



