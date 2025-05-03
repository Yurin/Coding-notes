#1007. Minimum Domino Rotations For Equal Row

## 🧠 Problem
In a row of dominoes, tops[i] and bottoms[i] represent the top and bottom halves of the ith domino. (A domino is a tile with two numbers from 1 to 6 - one on each half of the tile.)
We may rotate the ith domino, so that tops[i] and bottoms[i] swap values.
Return the minimum number of rotations so that all the values in tops are the same, or all the values in bottoms are the same.
If it cannot be done, return -1.

## 🧩 Approach
I check all numbers from 1 to 6 because each domino can have any value from 1 to 6 on the top or bottom.
If all top or bottom values can be made equal to a number x, I return the minimum number of rotations needed.

I check all numbers from 1 to 6 because each domino can have any value between 1 and 6 on its top or bottom.
For each number x, I check if it’s possible to make all the top or bottom values equal to x by rotating some dominos.
If it’s possible, I calculate how many rotations are needed and return the minimum number of rotations required to make all values the same.
If no such number exists, I return -1.
## 🕒 Time and Space Complexity
Time complexity: O(n) 
Space complexity: O(1) 
## 🤔 Notes

## 💻 Code (Python)
```python
class Solution(object):
    def minDominoRotations(self, tops, bottoms):
        for x in range(1, 7): 
            if all(x == t or x == b for t, b in zip(tops, bottoms)):
                return min(
                    sum(1 for t in tops if t != x), 
                    sum(1 for b in bottoms if b != x)
                )
        return -1

```