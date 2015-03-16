# Introduction #


Modern terminals are quite fast and powerful compared to the terminals ncurses was designed for. However, due to the nature of it's design, that does not mean ncurses will not behave poorly.

# Issues and Suggestions on How to Deal With Them #

## Flickering ##

A common problem is a flickering of the display. It's a good idea to look at the ncurses documentation to understand the underlying structures involved but if that's [tl;dr](http://en.wikipedia.org/wiki/Wikipedia:Too_long;_didn't_read) then here are two techniques you can use, depending on your situation:

  1. If you have many windows to display then you should not use Refresh(). Instead, you should call NoutRefresh() on each Window needing updating and finally call Update() to write the changes to the terminal.

  1. If you need to constantly clear the screen to properly update your windows, like if you are using Overlay(), then don't call Clear() or ClearkOk(). These functions force Goncurses to clear the terminal and then redraw the entire screen rather than simply updating what has changed. Instead, use Erase() to clear your window, update it, then refresh it (see above). This will let ncurses be more intelligent about updating the terminal.