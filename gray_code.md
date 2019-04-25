### What is Gray Code?
Gray code is an ordering of the binary numeral system such that two successive values differ in only one bit.  
For example we can have following ordering of all `2` bit integers `00 -> 01 -> 11 -> 10`.    
Here `00` and `01` differs in second bit, `01` and `11` differ in in first bit, `11` and `10` differ in second bit. Note that `10` and `00` differ in first bit, so this is circular i.e., last bit and first bit also need to differ by 1 bit.  
We can actually have more than one valid coding scheme for same number of bits. For example `00 -> 10 -> 11 -> 01` is also a valid coding.

### Constructing an *n*-bit gray code 
We will use recursion to accomplish this. Suppose we already know how to construct an *n-1* bit gray code. For example we will start with the above case for *n-1=2*. Here are the codes again  
`00`  
`01`  
`10`  
`11`  
Now if we insert `0` at the begining of all these strings we still have a valid gray code because they will still only differ on one bit (which they did before). But now we have *n* bit strings and we have already got half the required strings for *n* bit.  
`000`  
`001`  
`010`  
`011`  
How do we constructing the other half? Well that's easy. We just add `1` at the begining now.  
`100`  
`101`  
`110`  
`111`  
Are we done? If we just concatanate the above two lists we have  
`*000*`  
`001`  
`010`  
`**011**`  
`**100**`  
`101`  
`110`  
`**111**`  
We have moer than one bit difference in bold positions (first and last string also count). How do we fix this? Let's see what we know to be true so far. If we consider the list elements (I am going to use `0` based indexing so `000` is at index `0`, `001` is at index `1` and so on) we know these two sublists are already valid code `[0, 1, 2, 3], [4, 5, 6, 7]`. Now consider first elements of each list (that is `000` and `100`). To construct them we started with **same** string from the `n-1` bit code and for first one we added `0` and for the second one we added `1`. So these two also differ in only `1` bit position. Similarly it is true for last elements of two lists (`011` and `111`). So we know `[0, 1, 2, 3], [4, 5, 6, 7], [0, 4], [3, 7]` are all valid codes. I think at this point it quite obvious what we need to do. If we reverse the second list and concatanate it with first list we get `[0, 1, 2, 3, 7, 6, 5, 4]`. Here `3` is followed by `7` and `4` is followed by `0` (in circular sense) which are valid code. Rest of the list were already valid code. So we have actually generated a valid `3` bit gray code.  
`000`  
`001`  
`010`  
`011`  
`111`  
`110`  
`101`  
`100`   
Since we know how to make `n` bit code from `n-1` bit code and we know how to build `1` bit code `0->1` it follows that we can construct arbitrary length code using recursion.

