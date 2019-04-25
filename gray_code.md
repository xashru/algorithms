### What is Gray Code?
Gray code is an ordering of the binary numeral system such that two successive values differ in only one bit.  
For example we can have following ordering of all `2` bit integers `00 <-> 01 <-> 11 <-> 10`.    
Here `00` and `01` differs in second bit, `01` and `11` differ in in first bit, `11` and `10` differ in second bit. Note that `10` and `00` differ in first bit, so this is circular i.e., last string and first string also need to differ by 1 bit.  
We can actually have more than one valid coding scheme for same number of bits. For example `00 <-> 10 <-> 11 <-> 01` is also a `2` bit valid coding.

### Constructing an *n*-bit gray code 
We will use recursion to accomplish this. Suppose we already know how to construct an *n-1* bit gray code. For example we will start with the above case for *n-1=2*. Here are the codes again  
`00`  
`01`  
`10`  
`11`  
Now if we insert `0` at the beginning of all these strings we still have a valid gray code because they will still only differ on one bit (which they did before). But now we have *n* bit strings and we have already got half the required strings for *n* bit.  
`000`  
`001`  
`010`  
`011`  
How do we construct the other half? Well that's easy. We just add `1` at the beginning now.  
`100`  
`101`  
`110`  
`111`  
Are we done? If we just concatenate the above two lists we have  
**`000`**  
`001`  
`010`  
**`011`**  
**`100`**   
`101`  
`110`  
**`111`**  
We have more than one bit difference in bold positions (first and last string also count). In fact they differ in all three positions (`000<->111, 011<->100`). How do we fix this? Let's consider first elements of each half (that is `000` and `100`). To construct them we started with **same** string from the `n-1` bit code. For first one we added `0` and for the second one we added `1`. So these two differ in only `1` bit position. Similarly it is true for last elements of each half (`011` and `111`). I think at this point it quite obvious what we need to do. If we reverse the second half and concatenate it with first half we get `111` followed by `100` and last string becomes `100`. So we have managed to fix both the discrepancies we had before. As such we have actually generated a valid `3` bit gray code.  
`000`  
`001`  
`010`  
`011`  
`111`  
`110`  
`101`  
`100`   
Since we know how to make `n` bit code from `n-1` bit code and we know how to build `1` bit code `0<->1` it follows that we can construct arbitrary length code using recursion.

### Practice
https://leetcode.com/problems/gray-code/
