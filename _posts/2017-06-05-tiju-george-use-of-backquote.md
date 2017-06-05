---
layout: post
title: "Tiju George, Pythonic short way of reversing digits of a number with constraint"
date: 2017-06-05
---


##Python- Use of backquote a depreciated way as in python 3 for repr() and short way of solving a problem

Print reverse digits of an number. Note, The input is assumed to be a 32-bit signed integer. Your function should return 0 when the reversed integer overflows. 

```python
def reverse(x):
    number = int(x)
    flag = False
    if number < 0:
        flag = True
        #print flag
    reversenum = 0
    #print abs(number)
    
    while abs(number)>0:
        number = abs(number)
        remainder = number%10
        reversenum = (reversenum*10)+remainder
        number = number//10
    if (reversenum) > 2**(32-1):
        return 0
    elif reversenum < 2**(32-1)and flag is True:
        return -(reversenum)
    else:
        return reversenum
```
###Short way and showing usage of back quote
```python
def reverse(x):
    s = cmp(x, 0)
    r = int(`s*x`[::-1]) # or int(repr(s*x)[::-1])
    return s*r * (r < 2**31)
```
