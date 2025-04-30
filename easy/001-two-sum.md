# 1. Two Sum

## 🧠 Problem
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to `target`.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

## 🧩 Approach1
I used two loops to check all possible pair in the array.
For each element i, I calculate complement target - nums[i].
Then I loop again to see if there's another element j that matches the complement.
I also make sure i and j are not the same index.
Once I find a pair, I return their indices.

## 🕒 Time and Space Complexity
Time complexity: O(n²) → Because of the nested loops.
Space complexity: O(1) → No extra data structure used.

## 🤔 Notes
This approach works fine for small inputs, but it becomes slow with large arrays.

## 💻 Code (Python)
```python
def twoSum(self, nums, target):
    for i in range(len(nums)):
        part = target - nums[i]
        for j in range(len(nums)):
            if part == nums[j] and i != j:
                return[i,j]
    part = 0
```
## 🧩 Approach2
Use a hash map to store previously seen numbers and their indices.
For each number, calculate the complement (`target - num`).
If the complement exists in the hash map, return both indices.

## 🕒 Time and Space Complexity
Time complexity: O(n) 
Space complexity: O(n) 

## 💻 Code (Python)
```python
def twoSum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
```