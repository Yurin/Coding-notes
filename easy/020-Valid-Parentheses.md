20. Valid Parentheses

## 🧠 Problem
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

## 🧩 Approach
To solve this problem, we use a stack data structure. A stack follows the Last In First Out (LIFO) principle, which is perfect for matching brackets.
## 🕒 Time and Space Complexity
Time complexity: O(n) 
## 🤔 Notes

## 💻 Code (Python)
```python
def isValid
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    
    for char in s:
        if char in mapping:
            top_element = stack.pop() if stack else '#'
            if mapping[char] != top_element:
                return False
        else:
            stack.append(char)
    
    return not stack
```