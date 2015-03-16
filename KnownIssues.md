# Known Issues #

## All ##
  * won't install with a great many errors. This seems to be an issue with Go 1.3 and both the Linux and MacOS platforms. Make sure you upgrade to Go version 1.3.1 to fix this issue. Make users may need export CC=clang environmental variable.
  * garbled/odd output - This is likely due to using goroutines. Please see the [Concurrency](Concurrency.md) page for details.
  * Unicode/UTF-8 characters not displaying properly - There are a number of issues which may cause this. One, you need to make sure you version of curses has been compiled with UTF-8 support and that you're linking to the correct library which supports it. Second, you will need to call C's setlocale(LC\_ALL, "") prior to initializing Goncurses. This can be done via cgo or possibly some other third party Go library.
  * flickering - This is a big topic but the short answer is that it's probably not goncurses fault. Please see the page on [Optimizing](Optimizing.md) for tips to improving your Goncurses code.

## Linux ##
  * F1 key launches help and isn't captured by ncurses. This is not a goncurses issue nor an ncurses one and is commonly found by users running gnome-terminal. This is because the F1 key is mapped to the application and the event is captured by the Gtk bindings. It therefore is not propagated to the ncurses terminal layer. A temporary way to override this behavior would be to make a system call via exec calling gconf or gsettings (gnome 2 and 3 respectively) to override Apps->gnome-terminal->keybindings.

## Mac OSX ##
  * has\_mouse() undeclared - Goncurses is currently being tested against ncurses 5.9. As of this writing, OSX ships with ncurses 5.7 installed. Since this function was added in 5.8 it is recommended that you upgrade your version of ncurses in order to use Goncurses. There has been a recent fix pushed to tip that should prevent this error from happening however it is still recommended that you upgrade to ncurses 5.9.  It has been reported that MacPorts provides a working install of ncurses 5.9. If you choose to use homebrew to install a newer version of ncurses, cgo may still try to link against the older version depending on where and how homebrew installed ncurses. There are several solutions to overcoming this dilemma but it is up to the user to determine the best solution for their situation.
  * pkg-config not installed. Goncurses was changed to use pkg-config instead of providing static linker flags. This was done to ensure any changes in ncurses or system specific requirements for building ncurses programs. You will either need to install pkg-config or install goncurses from source and change the cgo commands to link to the libraries you want to use (thereby removing the pkg-config requirement).

## Windows ##
  * Will not build/install - Please see [Windows Installation](WindowsInstallation.md)
  * Form and Menu examples fail to build/run - Windows uses PDCurses and the menu and form extensions are not available to that library, they are strictly ncurses-only.