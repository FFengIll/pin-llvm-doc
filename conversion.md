# Conversion

指令转换，通过ASM到LLVM IR完成。

系统采用逐条asm转换的方式：
1. 读取将要执行的asm，由Pin在执行指令读取、插桩时完成
* 生成使用NativeX对象，并存储对应MCInst
* 转换NativeX对象为LLVM对象，包括module，function，block，Instruction，主要工作集中于llvm::Instruction的转换和生成
* 


转换功能由单一的函数接口提供，包含全局初始化、指令转换。

***

指令转换完全依照asm语义完成，因此，同asm一致，具有明确的入口与出口，  
*  entry: 
    *  memory
    *  register
*  exit: 
    *  memory
    *  register  

即，所有的中间指令的数据操作，均会有入口到出口，形成封闭的中间指令块。  



Support 8bit, 16bit, 32bit registers, like al, ah, ax and eax.  
Supported registers includes,
1.  eax
2.  ebx
3.  ecx
4.  edx
5.  ebp, esp, 

Flag convert can be used with argument controling.  
Supported flags includes,  
1.  zf
2.  sf
3.  of
4.  cf/bf 
5.  

