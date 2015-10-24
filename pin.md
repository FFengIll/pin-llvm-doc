# Pin

We use intel pin to implement the instrument functions.
Because of the great ability of pin, we can work more on the core - symbolic execution.

Pin can get the instructions of the testing programs, but it can only work on assemble instructions, like move, cmp, add, jump and etc.

If we want to process all of the assemble instructions, we have to work too much, so we want to convert the assemble to an IR instruction which we call Intermedia Representation. And we choosed LLVM IR.

Using the project "**MCSema**", we can complete the conversion between ASM and LLVM-IR and contain the semantics.

***
