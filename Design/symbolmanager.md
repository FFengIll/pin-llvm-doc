# SymbolManager

## Defination

用于存储IR中间变量的相关信息，包括：  
*   type
    *   addr: for address
    *   tmp: for IR tmp
    *   reg: for register
*   value
    *   store the value of the var which are get from the entry
    *   only load from entry, and no other calculation
2.  symbol
    *   addr, reg, tmp can be marked as a symbol
3.  id  
    *   each var with a type will comes with its unique id
    *   specially, tmp has its unique id only in current IR block
4.  extend
    *   a special pointer to extend the types
    *   directly source code editing is also available if it is necessary
*   width
    *   of course the width corresponding to the var
    *   Address (aka. Addr) is managed by 8 bit width only
    *   Register (aka. Reg) is managed by 32 bit, but a extra process can support other width within 32 bit

