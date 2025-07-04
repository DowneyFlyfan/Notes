# Number System & Sign Extension & Signed Number Arithmatic
1.  Number System: 在任一数制中，每一个数位上允许使用的记数符号的个数被称为该数制的Base。  
    每1位都对应1个表示该位在数码中的位置的值，这个值就称为数位的权值W。  
      
    
2.  Decimal -> Binary  
    ![](paste-3d12f515ee51381aa66d7755be6be31ef4fddc66.jpg)  
      
    
3.   Signed Decimal -> Binary & Signed Binary -> Decimal  
    先按1走，  
    然后 **1变0，0变1， 再+1**，得到有符号二进制数  
      
     **反之亦然  
    **  
    
4.  如果从8位转换成32位，需要  
      
    对于无符号数，直接补0  
    对于有符号数，直接补MSB (Maximum Significant Bit)  
      
    
5.  有符号数的加减法和无符号数相同  
      
    减 一个数 = 加上这个数的补码 ( 取反 + 1 )
