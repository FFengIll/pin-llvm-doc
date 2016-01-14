# SymbolManager

用于存储IR中间变量的相关信息，包括：  
*   type
    *   addr: for address
    *   tmp: for IR tmp
    *   reg: for register
*   value
    *   store the value of the variable which are get from the entry
    *   only load from entry, and no other calculation
2.  symbol
    *   addr, reg, tmp
3.  id  
4.  extend

