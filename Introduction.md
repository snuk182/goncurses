# Introduction #

GoNCurses is a Go language binding for the ncurses terminal library written in C. There is plenty of documentation to be found out in the wild for ncurses and those resources remain the best source of help if you are new to ncurses. However, several examples exist in the source code tree to help ease the learning curve. With the help of 'go doc', it should be possible to quite easily follow along with any C examples. By in large, you should find it much simpler and concise to use goncurses than the original C library.

# Pre-Installation #

GoNCuses requires ncurses 5.9. See '[Known Issues](KnownIssues.md)' and pkg-config.

# Installation #

## Go Release 1.x ##

Installation with the current Go release is done most simply with the `go` tool:

```
$go get code.google.com/p/goncurses
```


## Go 60.3 (old) ##

There is an hg branch in the goncurses tree called release.[r60](https://code.google.com/p/goncurses/source/detail?r=60) which contains code compatible with the 60.3 release of Go. This branch is no longer being maintained but contains functionality compatible with that release. Recent changes to ncurses will likely mean this code will not function without hacking some of the sources yourself. I highly encourage you to upgrade the the stable 1.0.x release of Go.