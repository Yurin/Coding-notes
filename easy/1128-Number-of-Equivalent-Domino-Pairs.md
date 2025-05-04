# 1128. Number of Equivalent Domino Pairs

## 🧠 Problem
Given a list of dominoes, dominoes[i] = [a, b] is equivalent to dominoes[j] = [c, d] if and only if either (a == c and b == d), or (a == d and b == c) - that is, one domino can be rotated to be equal to another domino.
Return the number of pairs (i, j) for which 0 <= i < j < dominoes.length, and dominoes[i] is equivalent to dominoes[j].

## 🧩 Approach
I change dominoes list to tuple so that I will find equal dominoes. And count the domino.

I convert each domino into a sorted tuple to treat [a, b] and [b, a] as the same. Then, I count the number of occurrences of each domino to find the number of equal pairs.
## 🕒 Time and Space Complexity
Time complexity: O(n) 
Space complexity: O() 
## 🤔 Notes

## 💻 Code (Python)
```python
class Solution(object):
    def numEquivDominoPairs(self, dominoes):
        norm = [tuple(sorted(d)) for d in dominoes]  
        count = Counter(norm)
        res = 0
        for v in count.values():
            if v >= 2:
                res += v * (v - 1) // 2
        return(res)
```