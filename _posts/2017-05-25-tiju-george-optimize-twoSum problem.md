---
layout: post
title: "Tiju George, Optimizing the complexity of TwoSum problem"
date: 2017-05-25
---


##Python- Two Sum explained better from O(n^2) to O(n)

Two Sum explained better from O(n^2) to O(n). In O(n^2) the solution is given as below:

```python
def twoSum(nums, target):
  for i in range(len(nums)):
    for j in range(len(nums)):
      if i==j:
        pass
      elif nums[i]+nums[j]==target:
        return [i, j]
print twoSum(nums, target)
```
###In O(n) the solution is given below with explanation
```python
def twoSum(self, nums, target):
  check = {}
  for i,num in enumerate(nums):
    if num not in check:
      check[target-num]=i
      #print "check and i is given as: ",check, i
    else:
      return [check[num],i]
```
Explanation:

Every time we check for the num in dictionary if it is not there we add the difference of target and checked num as new key in empty dictionary with value as old key so it becomes a pointer to current num the moment you see in future the difference-value in dictionary value.

For example:
Nums = [3, 2, 4, 1, 5]   target = 9

| i  | num  | new key i in dictionary   | value in dictionary corresponding to key i   |
|---|---|---|---|
| 0  |3   |6   |0   |
| 1  |2   |7   |1   |
| 2  |4   |5   |2   |
| 3  |1   |8   |3   |
| 4  |5   |    |    |


The moment it reaches num = 5 we have 5 as a key in dictionary pointing 2 in enumerate which has value 4 so we found the two sum in O(n) complexity.

