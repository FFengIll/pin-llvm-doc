# LLVM

LLVM用于提供IR指令，ASM到IR的转换，需要依赖于LLVM进行。

主要使用到了LLVM的MCInst指令，module，function，block，Instruction等特性。

ASM will convert into IR, like  
* load
* store
* binary operation
* casting
* branch