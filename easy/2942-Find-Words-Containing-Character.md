# 2942 Find Words Containing Character

## 🧠 Problem
You are given a 0-indexed array of strings words and a character x.
Return an array of indices representing the words that contain the character x.
Note that the returned array may be in any order.

## 🧩 Approach
This code checks all the words in the list and uses the in operator to see if the character is inside each word. If it is, the index is added to the result.
## 🕒 Time and Space Complexity
Time complexity: O(n) 
## 🤔 Notes

## 💻 Code (Python)
```python
class Solution(object):
    def findWordsContaining(self, words, x):
        result = []
        for i in range(len(words)):
            if x in words[i]:
                result.append(i)
        return result
```