# Conversion

指令转换，通过ASM到LLVM IR完成。

系统采用逐条asm转换的方式：
1. 读取将要执行的asm，由Pin在执行指令读取、插桩时完成
* 生成使用NativeX对象，并存储对应MCInst
* 转换NativeX对象为LLVM对象，包括module，function，block，Instruction，主要工作集中于llvm::Instruction的转换和生成
* 


转换功能由单一的函数接口提供，包含全局初始化、指令转换。