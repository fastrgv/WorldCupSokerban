![screenshot](https://github.com/fastrgv/WorldCupSokerban/blob/master/sokerban.png)

# WorldCupSokerban
This is a soccer-themed, 3D sokoban puzzle game that runs on Windows, Mac OS-X and GNU Linux

Click on the large tar.gz file under releases for all source & binaries, or try this link:

https://github.com/fastrgv/WorldCupSokerban/releases/download/v3.2.4/sb28nov18.tar.gz




# WorldCupSokerban
----------------------------------------------------------------

## What's new:

**ver 3.2.4 -- 26nov18**

* Now using sdl v207 uniformly on all platforms;
* Now using sfml v250 uniformly;
* Updated all sokoban solvers to enhance robustness & efficient solutions;


**ver 3.2.3 -- 08jul18**

* Updated to using SDL v2.0.7;
* Corrected code to handle DOS-formatted puzzle files.

**ver 3.2.2 -- 04jul18**

* Added & improved 2nd built-in solver initiated with numeric-keypad "=" key.  This might solve problems that stump the 1st solver [using the normal keyboard "=" key].
* Added a "Solution not found" message when a built-in solver fails within 10 seconds.
* Put Windows DLLs, EXEs into ./binw32/
* Updated AdaPng, AdaZLib;


## See complete revision history at end of file.


## WorldCupSokerban
This is a soccer-themed, 3D sokoban puzzle game that includes 2 external solvers and 1 embedded solver.

It has undo (u) and restart (r) functions.  Comes with many puzzle files, each typically having dozens of "levels".  The next (n) and previous (p) keys move between levels.  The (Lshft) and (Rshft) keys move between the different puzzle files (there are currently 60).  The (z) key creates a setpoint (reZero) so that subsequent restarts restore that setpoint.

To move the "pusher" use the arrow keys.  The objective is to kick all the red and blue balls into the goal nets.  Notice that these strange soccer balls roll in two perpendicular directions only!

And now the (=)-key triggers an embedded solver that helps you when you get stuck.

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
 * uses SFML for the sounds, SDL2 for input & window management;
 * fully OpenGL 3.3 core profile Ada code;
 * includes 2 autosolvers;

----------------------------------------------
## Embedded Autosolver Function
Two autosolvers are now embedded within this application so that pressing the ("=")-key at any time initiates an attempt by the primary solver to solve the present state of the current puzzle within a limited amount of time.  If successful then you will see an onscreen prompt to continue to press the equal-key to single-step toward the solution.  Otherwise you will see no such prompt.

Similarly, the 2nd alternate solver is initiated with the numeric keypad ("=")-key.

Thus, you can give yourself a headstart toward a correct solution by limited use of this feature.  Once you think you can solve it yourself, stop using the equal-key and proceed manually.  This really helps when you cannot see what your next move should be.

Embedded autosolver failure might imply the present state of the puzzle is impossible to solve, or simply that the autosolver failed due to time constraint, or insufficient capability.

## External Autosolvers
Remember that there are still two external autosolvers without time constraints.  Subject to several limitations, typing: "solver-name puzzle-file-name.sok maxlevels level-number" will attempt to solve a particular puzzle for you, where solver-name is either "ipuller3" or "ibox3".  There are many large or sparse [lishout] puzzles these solvers cannot handle, but they are pretty good at sovling the small dense ones.  Use the script ccc.sh to compile either solver for your operating system (assuming the presence of an Ada compiler).

The command to build them both [on OSX/linux] is simply:
	ccc.sh ibox3
	ccc.sh ipuller3

and on Windows:
	ccc.bat ibox3
	ccc.bat ipuller3

To run type:  [exeName puzzleFile TotalLevels LevelToSolve]

EG on windows type:
	binw32\ipuller3 games\pico_22.sok 22 3
	...to solve the 3rd level in file pico_22.sok.

EG on OSX type:
	ipuller3_osx games/pico_22.sok 22 3



----------------------------------------------
## what is special about this project?
Uses the Ada programming language and fully modern OpenGL methods, with textures, shaders and uniforms.  Achieves version 3.3 core profile contexts.  Compiles and runs on Windows, GNU/Linux and Mac OSX systems.

Focusing on portability and open source freedom, this project relies on a thin SDL2 binding from Dan Vazquez, a thin OpenGL binding from "Lumen", a PNG reader by Stephen Sanguine, and SFML-Audio (because of its elegant audio interface).



-----------------------
## Setup & Running:

Requires Windows, OSX or GNU/linux with a graphics card that supports OpenGL version 3.3;

Unzip the archive.

You will see a new directory appear, that you may rename.

Users should then cd to the install-directory, then, at the command line, type the executable name to start the game.

Windows users type binw32\sokerban.exe from the installation directory.

Linux users can type sokerban_gnu or double click the icon for sokerban_gnu in file manager.

Mac users note that this game may be initiated in two ways.  First, by opening a terminal, navigating to the install-directory, and typing sokerban_osx on the command line.  Second by navigating to the installation directory in Finder and clicking the "sokerban.app" icon named "Sokerban".  Note also that a 2-finger-swipe simulates the mouse wheel on a MacBook;  and a 2-finger click simulates the right button click to restore view settings, while a 1-finger click and drag simulates the left button drag on a mouse.

The install-directory should contain subdirectories named "data", "libs", and "games".


The GNU/linux executable must have access to ./libs unless your system already has the libraries it contains.  Then, at the command line type:

	sokerban_gnu ( or sokerban_osx, or sokerban.exe )

Remember, the WASD or arrow keys control movements.

The keyboard controls for view are:
* (c) closer
* (f) further
* (0) defaults
* (/) tilt up
* (\\) tilt down
* (=) try to autosolve
* (h) HELP

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
 * Xcode g++ compiler, if using OSX



================================================================
## Build instructions:

ccc.sh is the build script for the two autosolvers "puller" and "ibox".  Just type "ccc.sh puller" or "ccc.sh ibox" to compile on any platform, assuming the presence of a GNAT Ada compiler.

Three [pre-compiled] game executables are provided, one for Windows, one for gnu/linux and one for OSX.  The OSX executable is intended to have minimal runtime requirements:  sokerban_osx.  The linux binary sokerban_gnu, is intended to run in the presence of the directory "libLocal", which contains some dynamically loaded libraries that can be, but need not be present on a target system:
SDL2, SFML, FLAC, ogg, vorbis, & openal.

Similarly, the Windows binary, sokerban.exe, needs the DLLs collocated.

Three build scripts are described;  and due to a recent script change, a linux build machine need not have a C++ compiler installed.  Only GNAT is required.


-------------------------------------------------------
msWin32 => wcmp.bat

build script that requires libraries included in ./libs/win/.


-------------------------------------------------------
MacOSX:

<ocmpss.sh>:  build script for generating a portable executable that will run on most recent OSX platforms whether or not they have non-standard libraries such as GLEW, SDL2, SFML installed.  I used this to build the executable that I deliver, named sokerban_osx.  This script references delivered static library files for nonstandard libs.

------------------------------------------------------
GNU/Linux:  

<lcmpd.sh>:  utilizes the relocatable libraries that I deliver in this bundle under ./libs/.  I use this to build the gnu/linux executable that I deliver named sokerban_gnu, which should run in the presence of ./libs.

If the delivered linux binary does not run...

* Manually install GNAT GPL from libre.adacore.com/download/.
* Rerun the compile script lcmpd.sh.


### Fixable Link Problems during linux build:

On a linux build machine, you might have fixable link errors, depending on its configuration.  If you are missing "libz", you can simply copy "libz.so" from /usr/gnat/lib/gps/ into /usr/local/lib/.  If "libGL" cannot be found, this literally means "libGL.so" was absent.  But you might have "libGL.so.1" present.  In this case, simply create a softlink by changing to the libGL directory, then type the line:

sudo ln -s libGL.so.1 libGL.so  (and enter the admin password)

whence the linker should now be able to find what it wants.  But if there is more than one file libGL.so present on your system, make sure you use the best one;  i.e. the one that uses accelerated graphics.





---------------------------------
## legal mumbo jumbo:

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

**ver 3.2.1 -- 1apr18**

* Uninverted, improved font file;
* Improved function names in matutils;
* Too many undos no longer aborts;
* Added GPR build scripts;
* Improved & simplified OSX builds;


**ver 3.2.0 -- 11nov17**

* added prebuilt executables for msWindows;
* added working build scripts for msWindows;

* Updated build to use a) SFML v2.4.2;  b) AdaCore 2017;
* Added console startup messages with OGL profile & version;
* Removed unused libraries;  improved compile scripts;  
* Made code corrections;  added step, push count;
* Added IJKL-keys for movement as alternative to WASD, arrow keys.


**14may17, v3.1.9**
* Fixed logic error that caused vanishing sokerballs during rapid play;
* Paused key response during rolls;
* Improved input response.


**02may17, v3.1.8**
* Added step countdown during solve.
* Made corrections to autosolvers.


**23apr17, v3.1.8**

* Includes precompiled solvers for both platforms [osx,linux].
* Puzzle files are now sorted alphabetically for intuitive navigation.
* An autosolver is now embedded within this application so that pressing the "=" key at any time initiates an attempt to solve the present state of the current puzzle.  See extended description below.


**15apr17, v3.1.7**

* Now saves complete game state on exit.  Thus, your progress through the levels of each puzzle file is preserved.
* Better equilibration of sounds.
* Precompiled solvers for both platforms are contained in soksolvers.tar.gz


**7apr17, v3.1.6**

* Improved error checking in shader package;
* Removed OpenGL-deprecated functions that could cause aborts;
* Revised directory structure, simplified codes;


**3jan17, v3.1.5**

* Updated to use new SFML libs.
* Corrected a duplicate window glitch.
* Refined compiler scripts.


**30dec16, v3.1.4**

* Increased max # soccer balls to handle all puzzles.
* Now using generalized SFML-audio interface code: snd4ada.cpp.
* Added WASD keys for movement.
* Improved build system to be compatible with more linux distros.
* Improved OpenGL coding to also support Intel Skylake embedded graphics.


**16aug2016, v3.1.3**

* Improved code design of snd4ada.cpp.
* Next(n) and Prev(p) keys now move between the different puzzle levels while in single file test mode, just as in the normal mode.
* Now includes two, somewhat more refined, sokoban solvers written in Ada:  1) puller;  2) ibox.  These replace the CPP solver previously included.  Use the script "ccc.sh" to compile either in any O.S.


**12apr2016, v3.1.2**

* Important library update for Gnu/Linux users on 27% of distros that do not provide FLAC, ogg, vorbis libraries.  Missing softlinks caused run failure.  That is now fixed.


**20feb2016, v3.1.1**

* Added Mac binary bundle that acts like a typical Mac App.  This app is delivered in the installation directory, but could be moved elsewhere, such as your personal Applications directory [and initiated with a click].  Note that there are some soft [symbolic] links in the bundle that are resolved automatically when copied with the command "cp -r sokerban.app destination-directory".
* Generalized utex package.


**12jan2016, v3.1**

* Further improved man texture.
* Fixed error causing excessive field width.
* Moved puzzle centroid to center field.
* Closer key (c) now zooms directly toward center field.
* Refined key delay.
* Fixed single-file-mode, which was not working.
* Now puzzle names are read dynamically from the ./games/ directory, rather than being hardcoded.


**09jan2016, v3.0**

* Elliminated edge artifact on man texture.
* Added keyboard controls for view
	* (c) closer
	* (f) further
	* (d) defaults
	* (/) tilt up
	* (\\) tilt down


**09jan2016, v2.9**

* Pusher man now has a bit of an upward tilt.
* Mouse now controls game viewpoint.  The mouse wheel adjusts the eye distance;  a left button drag changes view angle;  a right button click restores the default view settings.  Now you can get much closer to the action!

**29nov2015, v2.8**

 * Improved PNG loader procedure now handles both RGBA and RGB image files for textures.
 * Discovered a non-repeatable problem of disappearing soccer-balls.  Clearing the variable namespace seems to have fixed it.
 * Revised goal sound logic.


**15nov2015, v2.7**

 * Transcribed from C++, this app is now written completely in the Ada language.
 * Revised pusher (thanks to Anders Widell).





