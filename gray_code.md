### What is Gray Code?
Gray code is an ordering of the binary numeral system such that two successive values differ in only one bit.  
For example we can have following ordering of all `2` bit integers `00 -> 01 -> 11 -> 10`.    
Here `00` and `01` differs in second bit, `01` and `11` differ in in first bit, `11` and `10` differ in second bit. Note that `10` and `00` differ in first bit, so this is circular i.e., last bit and first bit also need to differ by 1 bit.  
We can actually have more than one valid coding scheme for same number of bits. For example `00 -> 10 -> 11 -> 01` is also a valid coding.

### Constructing an *n*-bit gray code 
We will use recursion to accomplish this. Suppose we already know how to construct an *n-1* bit gray code. For example we will start with the above case for *n=2*. Here are the codes again
`00`  
`01`  
`10`  
`11`  
