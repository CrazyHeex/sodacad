---- About sodaCAD ----
=======================
An open source pattern making CAD suite, with capabilities similar to Optitex, Tukatech, or Gerber’s Accumark.

sodaCAD will support many advanced features such as pattern making, grading, and markers. 
The user interface will be user friendly for technical designers and pattern makers in the apparel and sewn product industries. 
sodaCAD is developed in a community-oriented, open environment. Users and developers are invited to contribute.

See www.sodacad.org

//The steps below have not yet been tested or updated for sodaCAD.

OS X Users
----------

If you use macports, see below. If you use brew, or neither one, use this section.

Install Homebrew from http://brew.sh/.

```
gcc --version # you'll need gcc 4.4 or newer. If yours is older:
brew tap homebrew/versions
brew options gcc48
brew install [flags] gcc48
mkdir ~/bin
cd ~/bin
ln -s /usr/local/bin/gcc-4.8 gcc
ln -s /usr/local/bin/g++-4.8 g++
ln -s /usr/local/bin/gcc-ar-4.8 gcc-ar
ln -s /usr/local/bin/gcc-nm-4.8 gcc-nm
ln -s /usr/local/bin/gcc-ranlib-4.8 gcc-ranlib
source ~/.bashrc
gcc --version # make sure it's 4.8. if it's not, ~/bin might not be on your path

brew install boost muparser qt

# Unzip or checkout a version of LibreCAD into a directory.
cd LibreCAD
./scripts/build-osx.sh
```

This creates an executable "LibreCAD.app/Contents/MacOS/LibreCAD" and package "LibreCAD.dmg".

OS X with MacPorts Users
-----------------------

install macports from http://www.macports.org/

After that install QT and a new gcc, which should version 4.4 or later.

Install a version of Qt, boost and muparser, for example
`$ sudo port install gcc46 qt4-creator-mac qt4-mac boost muparser`

Select the right compiler, as LibreCAD doesn't build with the default llvm-gcc42,
`$ sudo port select --set gcc mp-gcc46`

Unzip or checkout a version of LibreCAD into a directory.

```
cd LibreCAD
./scripts/build-osx.sh
```

This creates an executable "LibreCAD.app/Contents/MacOS/LibreCAD" and package "LibreCAD.dmg".

Users of Ubuntu/Debian and derivatives
--------------------------------------

Make sure you have the Qt version 4 development packages installed by
running the following commands:

```
$ sudo apt-get install g++ gcc make git-core libqt4-dev qt4-qmake libqt4-help \
qt4-dev-tools libboost-all-dev libmuparser-dev libfreetype6-dev pkg-config
```

Alternatively, you make sure you have deb-src lines enabled in your sources.list file, and run,

```
$ sudo apt-get build-dep librecad
```

For SVN see also: 
http://www.librecad.org/2010/10/debian-64-bit-and-ubuntu-compile-how-to/

For git see also:
http://librecad.org/cms/home/from-source/linux.html

Note that you will most likely need to run __qmake-qt4__ instead of just __qmake__.

Users of Red Hat and similar distibutions
-----------------------------------------

Install Qt, Boost and muParser development packages for your respective distribution;
EPEL(https://fedoraproject.org/wiki/EPEL) and similar repositories may come handy if
your base OS does not include the necessary packages.

As an example, for CentOS 6.4, after adding the EPEL repository,

```
yum groupinstall 'Desktop Platform Development' 'Development tools'
yum install qt-devel boost-devel muParser-devel
```

will install the necessary build dependencies.

Note that you will most likely need to run __qmake-qt4__ instead of just __qmake__.

FreeBSD users
-------------

Make sure you have the following ports installed:

```
x11-toolkits/qt4-gui devel/qt4-linguist devel/qt4-help-tools graphics/qt4-svg devel/boost-libs math/muparser
```

LibreCAD requires a C++11-capable compiler to build, Currently this means that one of

```
lang/gcc47, lang/gcc48, lang/gcc49 or lang/clang33
```

must be used.

Once these pre-requisites are satisfied, run the provided

```
scripts/build-freebsd.sh
```

See the script itself for some more options. Clang 3.3 does not yet work.

Windows Users
-------------

Building steps are also given at our wiki page:

http://wiki.librecad.org/index.php/LibreCAD_Installation_from_Source

A sample build batch file is included as scripts/build-windows.bat. If successful, this building script generates a Windows installer file using NSIS(http://nsis.sourceforge.net/Main_Page). 

- Download a copy of Qt SDK,  4.8.4 for example from http://qt-project.org/downloads 

- Download boost, from https://sourceforge.net/projects/boost/files/boost/
- unzip into C:\boost\, for example C:\boost\1_53_0 (in this directory you will find boost root directory, INSTALL, index, Jamroot etc.. etc).

- Download muParser 2.2.2 or later from http://sourceforge.net/projects/muparser/files/muparser/
- Create a directory named "muparser" in `C:\`
- Unzip muparser_v2_2_2.zip into `C:\muparser\`

Notes: At this point you will have the following directory structure: C:\muparser\muparser_v2_2_2\ (assuming you are using muparser-2.2.2). If you prefer to keep muParser in other locations, you should specify the directiory location with a custom.pro file in LibreCAD source folder, for example, the following setting is equivalent to the default muparser path in common.pro:

`MUPARSER_DIR = /muparser/muparser_v2_2_2`

- Start Qt Desktop using "Qt 4.8.4 for Desktop (MinGW)" shortcut.
- In Qt Desktop console, navigate to muParser build directory (C:\muparser\muparser_v2_2_2\build\), then type the following command to built muParser library:
  `mingw32-make -fmakefile.mingw`

After installation, start Qt Creator and load LibreCAD.pro,
from the build menu select "Build All".

Generic Unix Users
------------------

Unzip or checkout a version of LibreCAD into a directory.
```
cd LibreCAD
qmake librecad.pro
make
```
The executible is generated at "unix/librecad"
