### Use of Methods

This section covers some best practices for the use of methods in Interfaces.

#### Error Returns

In many programming languages (C in particular), it is common practice to define functions as having an integer return value that indicates whether the function concluded successfully (zero return value) or what went wrong (various non-zero return values). 

Do not use this practice for the definition of AllJoyn Interfaces. Instead, use AllJoyn's dedicated method error return mechanism. 

> **Methods should only conclude with a regular method return message (containing the declared output 
arguments) when the method has concluded successfully. If a method failed for some reason, the method should 
conclude by sending a method error return message, containing a well-defined error code.**

~~DISCUSSION~~
