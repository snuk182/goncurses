Installing Goncurses on Windows is not near as easy as on other platforms. You have been warned.

# Prerequisites #

  * A working copy of MinGW toolchain (Msys or Cygwin NOT required) that matches the architecture (32/64 bit) of the Go tools installed on your machine (NOT the architecture of your OS).
  * [PDCurses](http://pdcurses.sourceforge.net) 3.4 or higher installed and working. Earlier versions (confirmed with 2.5) are known not to work. The location of the C headers and libraries do not matter at this point.
  * [Mercurial SCM](http://mercurial.selenic.com)


# Installation #

  1. Clone goncurses either via 'go get' or 'hg clone':
    * _(easiest)_ go get -d code.google.com/p/goncurses
    * cd %GOPATH%\src & md code.google.com\p & hg clone http://code.google.com/p/goncurses code.google.com\p\goncurses
  1. overwrite the copy of curses.h distributed with PDCurses with the one located in the pdcurses sub-directory
  1. set CGO\_CFLAGS=-I path\to\pdcurses\headers
  1. set CGO\_LDFLAGS=-L path\to\pdcurses\libs
  1. go install

# Post Installation #

To run any programs build with Goncurses you will either need to:
  * Install pdcurses.dll into the same directory as any programs you wish to execute (recommended).
  * Make sure pdcurses.dll is in your working directory and launch the program from there.
  * Install pdcurses.dll into your system directory and register it so that Windows can find it.