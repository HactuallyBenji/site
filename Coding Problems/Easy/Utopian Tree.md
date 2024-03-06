The Utopian Tree goes through ___2___ cycles of growth every year. Each spring, it _doubles_ in height. Each summer, its height increases by ___1___ meter.

A Utopian Tree sapling with a height of ___1___ meter is planted at the onset of spring. How tall will the tree be after  growth cycles?

For example, if the number of growth cycles is ___n___ __=__ ___5___, the calculations are as follows:

```
Period  Height
0          1
1          2
2          3
3          6
4          7
5          14
```

**Function Description**

Complete the _utopianTree_ function in the editor below.

utopianTree has the following parameter(s):

- _int n_: the number of growth cycles to simulate

**Returns**

- _int:_ the height of the tree after the given number of cycles

**Input Format**

The first line contains an integer, ___t___, the number of test cases. ___t___ subsequent lines each contain an integer, ___n___, the number of cycles for that test case.

**Code**

```python
def utopianTree(n):

    # Write your code here
    isSpring = True
    treeHeight = 1
    
    for i in range(0, n):
        if isSpring:
            treeHeight *= 2
            isSpring = False
        else:
            treeHeight += 1
            isSpring = True

    return treeHeight
```