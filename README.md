![screenshot](https://github.com/fastrgv/WorldCupSokerban/blob/master/female.jpg)



# WorldCupSokerban
This is a soccer-themed, 3D sokoban puzzle game that runs on Windows, Mac OS-X and GNU Linux

Click on the large 7zip file under releases for all source & binaries, or try this link:

https://github.com/fastrgv/WorldCupSokerban/releases/download/v3.5.6/sb4mar21.7z




===================================================================================

soker-ban girl video link:
<https://youtu.be/No_ElhmToqw>

# World Cup Sokerban
----------------------------------------------------------------

## What's new:


**ver 3.5.6 -- 20feb21**
* Upgraded to using OpenAL sound.
* Updated existing autosolvers.
* Added more capable hbox4 autosolver.
* Added visual aid that shows 
	* possible destinations when a box is clicked.
	* possible sources when a goal is clicked.


**ver 3.5.5 -- 27oct20**
* Elliminated SFML-audio entirely.
* Greatly simplified build process.

**ver 3.5.4 -- 20sep20**
* Updated all glfw libs to v3.3.2.
* Added "sokerban.bat" for Windows users.


## See complete revision history at end of file.


## WorldCupSokerban Description
This is a soccer-themed, 3D sokoban puzzle game that includes 3 external solvers and 2 embedded solvers.

It has undo (u) and restart (r) functions.  Comes with many puzzle files, each typically having dozens of "levels".  The next (n) and previous (p) keys move between levels.  The (Lshft) and (Rshft) keys move between the different puzzle files (there are currently 60).  The (z) key creates a setpoint (reZero) so that subsequent restarts restore that setpoint.

To move the "pusher" use the arrow keys, ijkl keys, or wasd keys.  The objective is to kick all the red and blue balls into the goal nets.  Notice that these strange soccer balls roll in two perpendicular directions only!

The (=)-key or the (.)-key triggers an embedded solver that helps you when you get stuck.  You can single-step to a final solution, or to just part way toward the solution, in order to give you a hint. This feature is essential to learning to solve on your own.

The mouse can be used to control the game viewpoint.  The mouse wheel adjusts the eye distance;  a left button drag changes view angle;  a right button click restores the default view settings.  MacBooks can simulate these actions, as noted below.

Works on Macs running OSX and PCs running Windows or GNU/Linux.


--------------------------
## Features:
 * laptop friendly;
 * user definable puzzles;
 * many predefined puzzles ranging from easy to nearly impossible;
 * Windows, GNU/linux and OSX binaries included;
 * full source code;
 * supports high DPI mode on OSX Retina displays;
 * uses OpenAL for the sounds, GLFW3 for input & window management;
 * fully OpenGL 3.3 core profile Ada code;
 * includes 3 "live" embedded autosolvers that help you to learn;

----------------------------------------------
## Embedded Autosolver Function
Two autosolvers are now embedded within this application so that pressing the ("=")-key at any time initiates an attempt by the primary solver to solve the present state of the current puzzle within a limited amount of time.  If successful then you will see an onscreen prompt to continue to press the same key to single-step toward the solution.  Otherwise you will see no such prompt.  These embedded solvers are good for small and dense layouts;  but not so good at large, sparse puzzles.

Similarly, the 2nd alternate solver is initiated with the (".")-key.

Thus, you can give yourself a headstart toward a correct solution by limited use of this feature.  Once you think you can solve it yourself, stop using the equal-key and proceed manually.  This really helps when you cannot see what your next move should be.

Embedded autosolver failure might imply the present state of the puzzle is impossible to solve, or simply that the autosolver failed due to time constraint, or insufficient capability.

Finally, a single command-line argument (decimal float) specifies a persistent timeout interval to wait for the internal autosolver before giving up.  The default is 10.0 seconds.  A new setting remains in effect until a different setting is specified using a command-line argument. 


## External Autosolvers
Remember that there are still three external autosolvers without time constraints.  Subject to several limitations, typing: "solver-name puzzle-file-name.sok maxlevels level-number" will attempt to solve a particular puzzle for you, where solver-name is either "iplr3r", "ibox3r" or "hbox4".  There are many large or sparse [lishout] puzzles the first two solvers cannot handle, but they are pretty good at sovling the small dense ones.  Use the script ccc.sh to compile either solver for your operating system (assuming the presence of an Ada compiler).

The command to build them both [on OSX/linux] is simply:
	ccc.sh ibox3r
	ccc.sh iplr3r
	ccc.sh hbox4

and on Windows:
	ccc.bat ibox3r
	ccc.bat iplr3r
	ccc.bat hbox4

To run type:  [exeName puzzleFile TotalLevels LevelToSolve]

EG on windows type:
	binw32\iplr3r games\pico_22.sok 22 3
	...to solve the 3rd level in file pico_22.sok.

EG on OSX type:
	ibox3r_osx games/pico_22.sok 22 3

EG on linux type:
	hbox4_gnu games/pico_22.sok 22 3



----------------------------------------------
## what is special about this project?
It uses the Ada programming language and modern OpenGL methods, with textures, shaders and uniforms.  Compiles and runs on Windows, GNU/Linux and Mac OSX systems.

Focusing on portability, transparency, and open source freedom, this project relies exclusively on F.O.S.S. tools:  a thin GLFW3 binding, a thin OpenGL binding, a PNG reader by Stephen Sanguine & Dimitry Anisimkov, OpenAL Audio with a homebrew binding, and a GNAT compiler.



-----------------------
## Setup & Running:

Windows users should read "windows-setup.txt".
Mac users see "osx-setup.txt".


Requires Windows, OSX(>=10.13) or GNU/linux with a graphics card that supports OpenGL version 3.3;

Unzip the archive.  On Windows, 7z [www.7-zip.org] works well for this.
Open a commandline terminal, and cd to the install directory.

------------------------------------------------------------------------
Windows users may see some error messages (that may be ignored) pertaining to directory links.  Directory links are needed only on OSX & Linux.

You will see a new directory appear, that you may rename.

Users should then cd to the install-directory, then, at the command line, type the executable name to start the game.

Windows users type "sokerban.bat" from the installation directory.

------------------------------------------------------------------------
Linux users can type "sokerban_gnu" or double click the icon for sokerban_gnu in file manager.

The distributed linux executables require glibc v2.14 or newer.  That means if your distribution is older, it might not run, and you will need to recompile.

------------------------------------------------------------------------
Mac users note that this game may be initiated in two ways.  First, by opening a terminal, navigating to the install-directory, and typing "sokerban_osx" on the command line.  Second by navigating to the installation directory in Finder and clicking the "sokerban.app" icon named "Sokerban".  Note also that a 2-finger-swipe simulates the mouse wheel on a MacBook;  and a 2-finger click simulates the right button click to restore view settings, while a 1-finger click and drag simulates the left button drag on a mouse.

The install-directory should contain subdirectories named "data", "libs", and "games".


The GNU/linux executable must have access to ./libs unless your system already has the libraries it contains.  Then, at the command line type:

	sokerban_gnu ( or sokerban_osx, or sokerban.bat )

Remember, the WASD or IJKL or arrow keys control movements.

View Controls: 
* Your mouse can pan & zoom
* box-click:  possible destinations
* goal-click: possible sources

Also, the keyboard controls are:
* (c) zoom Closer
* (f) zoom Further
* (0) defaults
* (/) tilt up
* (\\) tilt down
* (=) try to autosolve (method #1 = iplr3r)
* (.) try to autosolve (method #2 = hbox4)
* (,) try to autosolve (method #3 = ibox3r)
* (h) HELP
* (b) Male Avatar (Boy)
* (g) Female Avatar (Girl)

Other controls, as indicated by the help screen:
* (esc) to quit
* (u) to undo
* (r) restart
* (n) next-level in current file
* (p) previous-level in current file
* (L-shift) previous file
* (R-shift) next file
* (z) reZero the setpoint

Note also that a specific sokoban file may be tested by naming it on the terminal window command line with the following syntax:

	sokerban sokfilepath maxlevels startlevel

where sokerban can be sokerban_gnu, sokerban_osx or sokerban.exe.

For example on linux you could type

	"sokerban_gnu games/original_50.sok 50 2"

to tackle level 2 from the original_50 sokoban file.  In this single-file mode, you can still use the next-level(n) & previous-level(p) keys, however, the next/previous files (R-shift/L-shift) keys are disabled.


================================================================
## Build Requirements:
 * a recent GNAT Ada compiler;
 * OpenGL 3.3 (or better) and a graphics card that supports it.
 * Xcode g++ compiler, if using OSX>=10.13(sep2017)



================================================================
## Build instructions:

ccc.sh is the build script for the two autosolvers "iplr3r" and "ibox3r".  Just type "ccc.sh iplr3r" or "ccc.sh ibox3r" to compile on any platform, assuming the presence of a GNAT Ada compiler.

Three [pre-compiled] game executables are provided, one for Windows, one for gnu/linux and one for OSX.  The OSX executable is intended to have minimal runtime requirements:  sokerban_osx.  The linux binary sokerban_gnu, is intended to run in the presence of the directory "libLocal", which contains some dynamically loaded libraries that can be, but need not be present on a target system:
GLFW3, SFML, FLAC, ogg, vorbis, & openal.

Similarly, the Windows binary, .\binw64\sokerban.exe, needs the DLLs collocated.

Three build scripts are described;  and due to a recent script change, a linux build machine need not have a C++ compiler installed.  Only GNAT is required.


-------------------------------------------------------
msWin64 => wbuildall.bat

build script that requires libraries included in ./binw64/


-------------------------------------------------------
MacOSX:

(ocmpss.sh):  build script for generating a portable executable that will run on most recent OSX platforms whether or not they have non-standard libraries such as GLEW, GLFW3, SFML installed.  I used this to build the executable that I deliver, named sokerban_osx.  This script references delivered static library files for nonstandard libs.

------------------------------------------------------
GNU/Linux:  

(lcmpd.sh):  utilizes the relocatable libraries that I deliver in this bundle under ./libs/.  I use this to build the gnu/linux executable that I deliver named sokerban_gnu, which should run in the presence of ./libs.

If the delivered linux binary does not run...

* Manually install GNAT GPL from libre.adacore.com/download/.
* Rerun the compile script lcmpd.sh.


### Fixable Link Problems during linux build:

On a linux build machine, you might have fixable link errors, depending on its configuration.  If you are missing "libz", you can simply copy "libz.so" from the AdaCore ~/lib/ directory into /usr/local/lib/.  If "libGL" cannot be found, this literally means "libGL.so" was absent.  But you might have "libGL.so.1" present.  In this case, simply create a softlink by changing to the libGL directory, then type the line:

sudo ln -s libGL.so.1 libGL.so  (and enter the admin password)

whence the linker should now be able to find what it wants.  But if there is more than one file libGL.so present on your system, make sure you use the best one;  i.e. the one that uses accelerated graphics.



---------------------------------
## License:

W.C.Sokerban itself is covered by the GNU GPL v3 as indicated in the sources:

 Copyright (C) 2015  <fastrgv@gmail.com>

 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.

 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.

 You may read the full text of the GNU General Public License
 at <http://www.gnu.org/licenses/>.


---------------------------------
## Media Files:

### General Note
The particular choice of sound and image files delivered are not essential to the function of the game and are easily replaced.  This software is primarily intended as a tutorial example of modern OpenGL methods.  The only requirements are that sounds be in WAV format and images be in PNG format.

### SoundFiles
Andres Cantor sound downloaded from YouTube and trimmed with FFMPEG.  Kick sound is from freesound.org so is covered by the Creative Commons Noncommercial License;  see
http://creativecommons.org/licenses/by-nc/3.0/legalcode/

### ImageFiles
...for textures were freely [no copyright indications] available on google images.  Files for text-textures were created using gimp and are also covered by the GNU GPL v3 license.  The pusher man is modified from a skin by Anders Widell, so thanks to Anders for that.  An alternate pusher is also available that was obtained from OpenGameArt.org and created by felixschuett with a CC0 license.


----------------------------------------------
## Best Download Site for all my games:
https://github.com/fastrgv?tab=repositories

Tags:  sokoban, puzzle, soccer, football


## Older Revision History:

**ver 3.5.3 -- 10jun20**
* Improved coding to read WAV file while "protected".
* Added onscreen feedback message when saving setpoint.


**ver 3.5.2 -- 3apr20**

* Improved linux sound system with no latency:  an Ada WAV-player using an Ada binding to the ALSA sound library.


**ver 3.5.1 -- 14mar20**

* Fixed broken Windows executables;
* Linux build now uses Ada tasking to reduce kick sound latency.


**ver 3.5.0 -- 20jan20**

* Significantly improved linux portability;




