# Instrument

Pin support the ability of dynamic instrument.
While the asm convert into llvm ir, we can call the methods of each ir instructions, and the methods can be called by Pin, then we can support a Run-time instrument based on LLVM IR.

插桩功能由Pin提供，在asm转为llvm ir后，针对每一条ir指令，调用对应的插桩功能函数，实现相应功能，而插桩函数由Pin调用完成，即实现二进制程序的运行时插桩


## IR instrument



## System call

### System call Entry    

### System call Entry