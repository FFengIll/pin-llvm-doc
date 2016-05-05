# Conversion

指令转换，完成ASM到LLVM IR的语义对应转换。  
Now support X86 32bit architecture only.

## Workflow

系统采用逐条asm转换的方式：
1. 读取将要执行的asm，由Pin在执行指令读取、插桩时完成
* 生成使用NativeX对象，并存储对应MCInst
* 转换NativeX对象为LLVM对象，包括module，function，block，Instruction，主要工作集中于llvm::Instruction的转换和生成
* 


转换功能由单一的函数接口提供，包含全局初始化、指令转换。


## Instruction ID

All instruction will come with its id which bind with its address. Id goes from 1 to max as need and will be refreshed for another instruction.

## Entry and Exit

指令转换完全依照asm语义完成，因此，同asm一致，具有明确的入口与出口，  
*  entry: 
    *  memory
    *  register
*  exit: 
    *  memory
    *  register  

即，所有的中间指令的数据操作，均会有入口到出口，形成封闭的中间指令块。  


## Register

Support 8bit, 16bit, 32bit registers, like al, ah, ax and eax.  
Supported registers includes,
1.  eax
2.  ebx
3.  ecx
4.  edx
5.  ebp, esp, 

## Flag

Flag convert can be used with argument controling.  
Supported flags includes,  
1.  zf
2.  sf
3.  of
4.  cf/bf 

In many situations, nothing will go with flags, so flag relevant convert can be controled with a switch argument.

## Instruction to IR
*   jmp
    *   load
    *   call: directly jmp will be treated as call, aka **1-path branch** without cc
*   ret
    *   esp
    *   eip
*   call
    *   load
    *   store: return addr, aka eip, but normally eip operation should not be seen
    *   call
*   mov
    *   load
    *   store
*   jcc
    *   load: load the flags that need to judge the cc
    *   cmp
    *   br: in llvm user br while meet a **2-path branch** with cc
*   add
    *   load
    *   add
    *   load: load flag that will change
    *   store: store new flags value into flags
    *   store
*   sub
    *   load
    *   sub
    *   load: load flag that will change
    *   store: store new flags value into flags
    *   store
*   mul
    *   load
    *   mul
    *   load: load flag that will change
    *   store: store new flags value into flags
    *   store
*   div
    *   load
    *   div
    *   load: load flag that will change
    *   store: store new flags value into flags
    *   store

## IR
*   store
    *   write value to reg: **store tmp_src, reg**
    *   write value to addr: **store tmp_src, tmp_dest**
*   load
    *   read value from reg: **tmp_dest = load reg**
    *   read value from addr (use tmp for addr): **tmp_dest = load tmp_src**
*   binary op
  *   arithmetic operator: add, sub, mul, div and etc
  *   logical operator: and, or, nor and etc
*   cast
*   shift
*   br - like **jmp in x86 asm**
*   call - like **call in x86 asm** but no balance of stack
*   cmp - an advance operator like **cmp in x86 asm**
    