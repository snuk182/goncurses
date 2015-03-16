# Introduction #
GoNCurses is an ncurses library for Google's Go language. It provides language bindings for the core ncurses library as well as the extended form, menu and panel libraries.

Goncurses is still in development and the API is not entirely stable. If at all possible, any breaking changes will be avoided. Once the vast majority (>80%) of ncurses has been implemented you can expect a lot more stability.

If you run into any problems, please see the [Known Issues](KnownIssues.md) section of the wiki prior to filing an issue report to make sure it hasn't already been covered.

_**Windows users**_ please see the wiki for [Windows Installation](WindowsInstallation.md) for prerequisites and installation instructions.

# Prerequisites #

  * Working pkg-config installed
  * Ncurses 5.9 development libraries installed (Mac users - ncurses 5.9.20110404 from [Mac Ports](http://www.macports.org) should work.)

# Installation #
```
$go get code.google.com/p/goncurses
```

# Current Status #

Goncurses is in a fairly usable state. Most, if not all, of the core functions have been implemented already and many of the remaining functions have either a niche use or are duplicate features from other functions.

If you find any missing functionality please submit a bug report with your request and it will likely get implemented in a timely fashion. Alternatively, you can also submit a pull request via the issue tracker to add what you need. See contributing in the wiki for more information.