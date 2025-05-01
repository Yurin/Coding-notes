# 2071. Maximum Number of Tasks You Can Assign

## 🧠 Problem
You have n tasks and m workers. Each task has a strength requirement stored in a 0-indexed integer array tasks, with the ith task requiring tasks[i] strength to complete. The strength of each worker is stored in a 0-indexed integer array workers, with the jth worker having workers[j] strength. Each worker can only be assigned to a single task and must have a strength greater than or equal to the task's strength requirement (i.e., workers[j] >= tasks[i]).Additionally, you have pills magical pills that will increase a worker's strength by strength. You can decide which workers receive the magical pills, however, you may only give each worker at most one magical pill.Given the 0-indexed integer arrays tasks and workers and the integers pills and strength, return the maximum number of tasks that can be completed.

## 🧩 Approach1
We first sort the two 0-indexed integer arrays: tasks and workers in ascending order.
Then, we iterate through the sorted tasks and try to assign each one to the weakest available worker.
If the current worker's strength is greater than or equal to the task's requirement, we assign the task directly.
If not, we check whether giving the worker a pill (which increases their strength by strength) would allow them to handle the task. If so, we assign the task and decrease the number of available pills by one.
Otherwise, we skip to the next worker.
We repeat this process until either we run out of tasks, workers, or pills.

## 🕒 Time and Space Complexity
Time complexity: O(n log n + m log m) 
Space complexity: O(1) 
## 🤔 Notes
❌ Why This Approach1 May Fail
This greedy approach compares tasks and workers in order from weakest to strongest, assigning tasks as soon as a worker is strong enough — either naturally or with a pill.
However, this method does not guarantee an optimal assignment because:
A weak worker might be given a pill early to complete an easy task, but a stronger task later may no longer be doable even with a pill.
We do not consider the possibility that saving pills for harder tasks or assigning stronger workers to harder tasks might allow us to complete more tasks overall.
The approach lacks global planning — it makes local decisions for each task without checking whether this leads to the best total outcome.
Therefore, although simple and fast, this approach may leave some tasks unassigned that could have been completed with better resource allocation.
## 💻 Code (Python)
```python
class Solution(object):
    def maxTaskAssign(self, tasks, workers, pills, strength):
        tasks.sort()
        workers.sort()
        output = 0
        j = 0  

        for i in range(min(len(tasks), len(workers))):
            if tasks[i] <= workers[j]:
                output += 1
                j += 1
            elif pills > 0:
                if tasks[i] <= workers[j] + strength:
                    output += 1
                    pills -= 1
                    j += 1
                else:
                    j += 1
            else:
                j += 1

        return output

```
## 🧩 Approach2
I haven't fully understood this approach yet, so I'll write it up tomorrow.
## 💻 Code (Python)
```python
class Solution(object):
    def maxTaskAssign(self, tasks, workers, pills, strength):
        tasks.sort()
        workers.sort()
        left, right = 0, min(len(tasks), len(workers))

        while left < right:
            mid = (left + right + 1)//2
            usedPills = 0
            avail = workers[-mid:]            
            canAssign = True

            for t in reversed(tasks[:mid]):
                if avail[-1] >= t:
                    avail.pop()
                else:
                    idx = bisect.bisect_left(avail, t - strength)
                    if idx == len(avail) or usedPills == pills:
                        canAssign = False
                        break
                    usedPills += 1
                    avail.pop(idx)

            if canAssign:
                left = mid
            else:
                right = mid - 1

        return left
```