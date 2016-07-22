![screenshot](https://github.com/fastrgv/WorldCupSokerban/blob/master/sokerban.png)

# WorldCupSokerban
This is a soccer-themed, 3D sokoban puzzle game that runs on Mac OS-X and GNU Linux

Click on the large tar.gz file under releases for all source & binaries.


# WorldCupSokerban  v3.1.2
----------------------------------------------------------------

## Changes (newest @ top):


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
 * Comes with an autosolver <trbfs.cc>


## what is special about this project?
Uses the Ada programming language and fully modern OpenGL methods with textures, shaders and uniforms.  Achieves version 3.3 core profile contexts, and compiles and runs on both GNU/Linux and Mac OS-X systems.  This project serves as a testbed for learning the complexities of modern OpenGL and GLSL.

Focusing on portability and freedom, no coding effort or compromise has been made to accomodate proprietary operating systems.  It relies on a thin SDL2 binding from Dan Vazquez, a thin OpenGL binding from "Lumen", a PNG reader by Stephen Sanguine, and SFML-Audio (because of its elegant audio interface).



This is a soccer-themed, 3D sokoban puzzle game.  It uses data in a format that is commonly found on the internet.

It has undo (u) and restart (r) functions.  Comes with many puzzle files, each typically having dozens of "levels".  The next (n) and previous (p) keys move between levels.  The (Lshft) and (Rshft) keys move between the different puzzle files (there are currently 60).  The (z) key creates a setpoint (reZero) so that subsequent restarts restore that setpoint.

To move the "pusher" use the arrow keys.  The objective is to kick all the red and blue balls into the goal nets.  Notice that these strange soccer balls roll in two perpendicular directions only!

And now the mouse can be used to control the game viewpoint.  The mouse wheel adjusts the eye distance;  a left button drag changes view angle;  a right button click restores the default view settings.  MacBooks can simulate these actions, as noted below.

Works on Macs running OS-X and PCs running GNU/Linux.


--------------------------
## Features:
 * laptop friendly;
 * user definable puzzles;
 * many predefined puzzles ranging from easy to impossible/ridiculous;
 * both GNU/linux and OSX binaries;
 * full source code;
 * supports high DPI mode on OS-X Retina displays;
 * uses SFML for the sounds, SDL2 for input & window management;
 * fully OpenGL 3.3 core profile Ada code;

----------------------------------------------
## Build Requirements:
 * a recent GNAT Ada compiler;
 * OpenGL 3.3 (or better) and a graphics card that supports it.


## Build instructions:

Two [pre-compiled] binary executables are provided, one for gnu/linux and one for OS-X.  The OSX executable is intended to have minimal runtime requirements:  sokerban_osx.  The other binary [for linux] sokerban_gnu, is intended to run in the presence of the directory "libLocal", which contains some dynamically loaded libraries that can be, but need not be present on a target system:  GLEW, SDL2, SFML.

Two build scripts are described:

-------------------------------------------------------
MacOSX => ocmp.sh:

build script for generating a portable executable that will run on most recent OS-X platforms whether or not they have non-standard libraries such as GLEW, SDL2, SFML installed.  I used this to build the executable that I deliver, named sokerban_osx.  This script references delivered static library files for nonstandard libs.

------------------------------------------------------
GNU/Linux => lcmp.sh:

utilizes the relocatable libraries that I deliver in this bundle under ./libs/.  I use this to build the gnu/linux executable that I deliver named sokerban_gnu, which should run in the presence of ./libs.

If it doesn't run on your linux distro, you will have to try to build the executable yourself.  In that case, it is hoped that this script <lcmp.sh> will work for you.  The intent was to provide all the needed interface/include files under ./incLocal/ and all the nonstandard relocatable libraries under ./libLocal/.


-----------------------
## Running:

Requires OS-X or GNU/linux with a graphics card that supports OpenGL version 3.3;

Unzip the archive and you will see a new directory appear with a name like (bundle+date), that you should rename to something like (install_directory).  

Users should then cd to (install_directory), then, at the command line, type the executable name to start the game.

Mac users please note:  this game is initiated by opening a terminal, navigating to the (install_directory), and typing the executable-name on the command line.  Note also that a 2-finger-swipe simulates the mouse wheel on a MacBook;  and a 2-finger click simulates the right button click to restore view settings, while a 1-finger click and drag simulates the left button drag on a mouse.

The (install_directory) should contain subdirectories named "data", "libs", and "games".


The GNU/linux executable must have access to ./libs unless your system already has the libraries it contains.  Then, at the command line type:

	sokerban_gnu ( or sokerban_osx )

Remember, the arrow keys control movements and the keyboard controls for view are:
* (c) closer
* (f) further
* (d) defaults
* (/) tilt up
* (\\) tilt down


Finally, subject to several limitations, typing: "trbfs puzzle-file-name.sok maxlevels level-number" will attempt to solve a particular puzzle for you.  There are many cases this solver cannot handle, but it is pretty good at sovling certain types of puzzles, particularly the more dense ones.  It is not very good at the near-Lishout type, if you know what that means.

-----------------------------------------------------------------

Please send questions or comments to fastrgv@gmail.com


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
