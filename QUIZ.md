### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
The dev board works via a message reciver, so the code waits for a signal then processes that signal as opposed to the usual method of constantly analyzing incoming bytes. This makes the message system car more efficient.  


### What does `detached_callback` do? What would happen if it wasn't used?
Detached callback should prevent the code from being delayed by a thread by making them run seperatly from the main program. This prevents the UI from freezing while the detatched threads run their course. 


### What does `LockedSerial` do? Why is it _necessary_?
Lock serial is key for the detached callbacks to work, as it locks the serial data and only allows one thread to work on it at a time. This prevents errors from multiple detached threads trying to do the same thing at the same time.
