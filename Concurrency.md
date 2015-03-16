# Introduction #

ncurses wasn't designed with concurrency in mind when it was created. Naturally, this is an issue when using ncurses in a concurrent language like Go. If two or more goroutines attempt to write to the same window, or read and write input from the same window, you can cause corruption in the underlying C struct. If you're lucky this will only cause odd behaviour in the screen ouput. This article will attempt to help you overcome these limitations.


# ncurses Threading Support #

ncurses does have a build-in global mutex locking system. It hasn't, however, been implemented into goncurses at this time nor does it appear to be widely used. It is currently being evaluated whether this will be implemented or whether Go's natural solutions actually provide a better end result than the native one.


# Select #

Use a select statement and channels to provide a natural locking mechanism. This may make implementing the code which provides screen updates/output more difficult to write but will provide a much better solution than that of a mutex, which is complicated in its own way.


# Global Mutex #

This is a simple solution which can be implemented fairly easily. Using Go's mutex's from the standard library you can lock sections of code to ensure that writes happen atomically. This requires using a global mutex which you Lock before executing any code which reads from or writes to any window and then Unlocking again after you're done.

Since GetChar and relating functions are connected to the underlying C Window structure you will need to ensure you don't attempt to write to the window via a Print at the same time. Since these input functions can block while awaiting input you'll have to be diligent about handling the mutex so as not block any output (perhaps via polling or a timeout) causing the program to hang. Essentially, the system will be deadlocked until input is received. For this reason I don't believe this is the ideal way to handle this problem.