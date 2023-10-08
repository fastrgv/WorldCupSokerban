![screenshot](https://github.com/fastrgv/WorldCupSokerban/blob/master/female.jpg)



# WorldCupSokerban
This is a soccer-themed, 3D sokoban puzzle game that runs on Windows, Mac OS-X and GNU Linux

Click on the large 7zip file under releases for all source & binaries, or try this link:

https://github.com/fastrgv/WorldCupSokerban/releases/download/v3.6.2/sb24sep22.7z

Type "7z x filename" to extract the archive.

### GitHub Note: Please ignore the "Source code" zip & tar.gz files. (They are auto-generated by GitHub). Click on the large 7z file under releases to download all source & binaries (Windows & Linux). Then, type "7z x filename" to extract the archive. 



===================================================================================

soker-ban girl video link:
<https://youtu.be/No_ElhmToqw>




video soker-ban girl:
<https://youtu.be/No_ElhmToqw>

# World Cup Sokerban

----------------------------------------------------------------

## What's new:



**ver 3.6.3 -- 7oct2023**

* New OSX build without bundle, & without using Xcode.
* Updated splaytree code for solvers.


**ver 3.6.2 -- 24sep2022**

* Removed w32 build because embedded solvers need maximal memory.
* Now using simpler-to-setup GNU Ada for Win64.


**ver 3.6.1 -- 16sep2022**

* Now using GNU Ada rather than defunct AdaCore compiler.
* Added several new puzzle groups including Loma.


## See complete revision history at end of file.


## WorldCupSokerban Description
This is a soccer-themed, 3D sokoban puzzle game that includes 3 external solvers and 3 embedded solvers.

It has undo (u) and restart (r) functions.  Comes with many puzzle files, each typically having dozens of "levels".  The next (n) and previous (p) keys move between levels.  The (Lshft) and (Rshft) keys move between the different puzzle files (there are currently 60).  The (z) key creates a setpoint (reZero) so that subsequent restarts restore that setpoint.

To move the "pusher" use the arrow keys, ijkl keys, or wasd keys.  The objective is to kick all the red and blue balls into the goal nets.  Notice that these strange soccer balls roll in two perpendicular directions only!

The (=)-key or the (.)-key or the (,)-key triggers embedded solvers that helps you when you get stuck.  You can single-step to a final solution, or to just part way toward the solution, in order to give you a hint. This feature is essential to learning to solve on your own.

The mouse can be used to control the game viewpoint.  The mouse wheel adjusts the eye distance;  a left button drag changes view angle;  a right button click restores the default view settings.  

Works on PCs running Windows, OSX, or GNU/Linux.


--------------------------
## Features:
 * laptop friendly;
 * user definable puzzles;
 * many predefined puzzles ranging from easy to nearly impossible;
 * Windows, OSX, GNU/linux binaries included;
 * full source code;
 * uses OpenAL for the sounds, GLFW3 for input & window management;
 * fully OpenGL 3.3 core profile Ada code;
 * includes 3 "live" embedded autosolvers that help you to learn;

 * no installation
 * no dependencies
 * simply unzip in your Downloads directory, and run.
 * or unzip onto a USB flash drive [w/same file format] and run.

----------------------------------------------
## Embedded Autosolver Function
Three autosolvers are now embedded within this application so that pressing the ("=")-key at any time initiates an attempt by the primary solver [puller] to solve the present state of the current puzzle within a limited amount of time.  If successful then you will see an onscreen prompt to continue to press the same key to single-step toward the solution.  Otherwise you will see no such prompt.  These embedded solvers are good for small and dense layouts;  but not so good at large, sparse puzzles.

Similarly, the 2nd alternate solver [hbox4] is initiated with the (".")-key.
And the 3rd alternate solver [ibox] is initiated with the (",")-key.

Thus, you can give yourself a headstart toward a correct solution by limited use of this feature.  Once you think you can solve it yourself, stop using the equal-key and proceed manually.  This really helps when you cannot see what your next move should be.

Embedded autosolver failure might imply the present state of the puzzle is impossible to solve, or simply that the autosolver failed due to time constraint, or insufficient capability.

Finally, a single command-line argument (decimal float) specifies a persistent timeout interval to wait for the internal autosolver before giving up.  The default is 10.0 seconds.  A new setting remains in effect until a different setting is specified using a command-line argument. 


## External Autosolvers
Remember that there are still three external autosolvers without time constraints.  Subject to several limitations, typing: "solver-name puzzle-file-name.sok maxlevels level-number" will attempt to solve a particular puzzle for you, where solver-name is either "iplr3r", "ibox3r" or "hbox4".  There are many large or sparse [lishout] puzzles the first two solvers cannot handle, but they are pretty good at sovling the small dense ones.  Use the script ccc.sh to compile either solver for your operating system (assuming the presence of an Ada compiler).

The command to build them all on linux is simply:
	cccgnu.sh ibox3r
	cccgnu.sh iplr3r
	cccgnu.sh hbox4

On Windows use ccc.bat.
On Mac/OSX use cccosx.sh


To run type:  [exeName puzzleFile TotalLevels LevelToSolve]

EG on windows type:
	binw64\iplr3r games\pico_22.sok 22 3
	...to solve the 3rd level in file pico_22.sok.


EG on linux type:
	hbox4 games/pico_22.sok 22 3

EG on OSX type:
	ibox3r_osx games/pico_22.sok 22 3



----------------------------------------------
## what is special about this project?
It uses the Ada programming language and modern OpenGL methods, with textures, shaders and uniforms.  Compiles and runs on Windows, OSX, GNU/Linux systems.

Focusing on portability, transparency, and open source freedom, this project relies exclusively on F.O.S.S. tools:  a thin GLFW3 binding, a thin OpenGL binding, a PNG reader by Stephen Sanguine & Dimitry Anisimkov, OpenAL Audio with a homebrew binding, and a GNAT compiler.



-----------------------
## Setup & Running:

Mac/OSX users should read "osx-setup.txt".
Windows users should read "windows-setup.txt".

Unzip the archive.  

* On Linux & Windows, 7z [www.7-zip.org] works well for this. The proper command to extract the archive and maintain the directory structure is "7z x filename".

* On OSX, Keka handles 7z files.  The command-line for Keka works thusly:
	* /Applications/Keka.app/Contents/MacOS/Keka --cli 7z x (filename.7z)

After the archive is unzipped...

------------------------------------------------------------------------
Open a commandline terminal, and cd to the install directory.

You will see a new directory appear, that you may rename.

Users should then cd to the install-directory, then, at the command line, type the executable name to start the game.


------------------------------------------------------------------------
Mac users type:

	sokerban_osx

------------------------------------------------------------------------
Windows users type "sokerban.bat" from the installation directory. Or to set the standard default of 10 seconds wait before giving up for internal solvers type:
	binw64\sokerban.exe 10.0

------------------------------------------------------------------------
Linux users can type:

	sokerban_gnu

or double click the icon for sokerban in file manager. Here too, sokerban 10.0 sets internal solver wait to 10 seconds.

You can also run the windows EXEs under wine thusly:

	* wine cmd < sokerban.bat
	* wine binw64/sokerban.exe

Note: I suggest that Windows users DO NOT try running the linux executables under WSL [Windows Subsystem for Linux]; that mode is not supported. Simply use the windows version.

**If an older Linux system complains that /dev/dsp/ cannot be opened, prepend the command with "padsp",EG:  "padsp (ExeName)".**



------------------------------------------------------------------------

The install-directory should contain subdirectories named "data", "libs", and "games".


The GNU/linux executable must have access to ./libs unless your system already has the libraries it contains.  Then, at the command line type:

	sokerban ( sokerban.bat )

Remember, the WASD or IJKL or arrow keys control movements.

View Controls: 
* Your mouse can pan & zoom
* box-click:  possible destinations
* goal-click: possible sources

Also, the keyboard controls are:
* (c) zoom Closer
* (f) zoom Further
* (o) zoom default
* (/) tilt up
* (\\) tilt down
* (=) try to autosolve (method #1 = iplr3r)
* (.) try to autosolve (method #2 = hbox4 => most capable)
* (,) try to autosolve (method #3 = ibox3r)
* (h) HELP
* (b) Male Avatar (Boy)
* (g) Female Avatar (Girl)

Other controls, as indicated by the help screen:
* (esc) to quit
* (u) to undo
* (r) reset@setPt;   (1) restart puzzle
* (n) next-level in current file
* (p) previous-level in current file
* (L-shift) previous file
* (R-shift) next file
* (z) reZero the setpoint

Note also that a specific sokoban file may be tested by naming it on the terminal window command line with the following syntax:

	<sokerban> sokfilepath maxlevels startlevel

where <sokerban> can be 
	sokerban_gnu, sokerban_osx or sokerban.bat.

For example on linux you could type

	"sokerban_gnu games/original_50.sok 50 2"

to tackle level 2 from the original_50 sokoban file.  In this single-file mode, you can still use the next-level(n) & previous-level(p) keys, however, the next/previous files (R-shift/L-shift) keys are disabled.


================================================================
## Build Requirements:
 * a recent GNAT Ada compiler;
 * OpenGL 3.3 (or better) and a graphics card that supports it.



================================================================
## Build instructions:

ccc.sh/ccc.bat are the build scripts for the autosolvers "hbox4", "iplr3r" and "ibox3r".


The following build scripts work for GNU Ada [with its own g++].


-------------------------------------------------------
msWin64 => setpath64.bat + wbuildall.bat

build script that requires libraries included in ./binw64/
Please read ~/docs/gnuAdaOnWindows.txt.


------------------------------------------------------
Mac/OSX => obuildall.sh

------------------------------------------------------
GNU/Linux:  

(lbuildall.sh):  utilizes the relocatable libraries that I deliver in this bundle under ./libs/.  I use this to build the gnu/linux executable that I deliver named sokerban, which should run in the presence of ./libs.

If the delivered linux binary does not run...

* Manually install GNU Ada compiler. See "gnuAdaOnWindows.txt".
* Rerun the compile script lbuildall.sh.





---------------------------------
## License:

W.C.Sokerban itself is covered by the GNU GPL v3 as indicated in the sources:

 Copyright (C) 2023  <fastrgv@gmail.com>

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

It is my intention to use media with copyrights or licenses that are compatible with GPLv3. Please notify me if you believe there is an incompatibility, and it will be removed ASAP, eg a CC-by-NC license is NOT GPL compatible.



### SoundFiles
Andres Cantor sound downloaded from YouTube and trimmed with FFMPEG.  Kick sound is from freesound.org so is covered by the Creative Commons CC0 License;  see the file creativeCommons.txt.

### ImageFiles
...for textures were freely [no copyright indications] available on google images.  Files for text-textures were created using gimp and are also covered by the GNU GPL v3 license.  The pusher man is modified from a skin by Anders Widell, so thanks to Anders for that.  An alternate pusher is also available that was obtained from OpenGameArt.org and created by felixschuett with a CC0 license.


----------------------------------------------
## Download Site for all my games:
https://github.com/fastrgv?tab=repositories
https://www.indiedb.com/members/fastrgv/games
https://fastrgv.itch.io
https://sourceforge.net/u/fastrgv/profile/
https://gamejolt.com/@fastrgv/games

## Tags:  sokoban, puzzle, soccer, football


## Older Revision History:

**ver 3.6.0 -- ddmmm2021** (not delivered)
* Updated all GLFW libs to newer [static] version, & scripts.
* Removed cc-by-nc-licensed puzzles due to incompatibility with GPLv3.

**ver 3.5.9 -- 29oct2021**
* Improved adaOpenAL binding code...sokerban is now buildable with [GNU Compiler Collection] GNAT, as well as all AdaCore versions.
* Updated glext.lib.

**ver 3.5.8 -- 14oct21**
* 1-key now restores Original puzzle.
* Added standard close window event handler.
* Improved undo function.
* Updated libraries.

**ver 3.5.7 -- 24mar21**
* Repaired Rt.MouseBtn function to un-highlight [only].

**ver 3.5.7 -- 4mar21**
* Added 3rd embedded solver accessed by (,)-key.

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


