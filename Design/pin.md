# Pin

We use **Intel pin** to implement the instrument functions.
Because of the great ability of pin, we can work more on the core - symbolic execution.

Pin can get the instructions of testing programs, but it can only work on assemble instructions, like move, cmp, add, jump and etc.

If we want to process all of the assemble instructions, we have to work too much, so we want to convert the assemble to an IR instruction which we call Intermedia Representation. And we choosed LLVM IR.

Using the project "**MC-Sematics**", we can complete the conversion between ASM and LLVM-IR. The conversion can contain the instruction functions and semantics.

***

## Unsupported
Now some APIs of Pin are not supported!  
Pin defined many APIs but has not complete all of them now!  