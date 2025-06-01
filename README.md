# AOA Module-23
## Day 1 - Minimum Cost Path 
### Write a python program to Implement Minimum cost path using Dynamic Programming.
```py
def min_cost_path(cost):
    m, n = len(cost), len(cost[0])

    for i in range(m):
        for j in range(n):
            if i == 0 and j == 0:
                continue
            top = cost[i-1][j] if i > 0 else float('inf')
            left = cost[i][j-1] if j > 0 else float('inf')
            diag = cost[i-1][j-1] if i > 0 and j > 0 else float('inf')
            cost[i][j] += min(top, left, diag)

    return cost[m-1][n-1]


# Example usage
cost_matrix = [
    [1, 2, 3],
    [4, 8, 2],
    [1, 5, 3]
]

print(min_cost_path(cost_matrix))

```
## Day 2 - Coin Change Problem
### Create a Python Function to find the total number of distinct ways to get a change of 'target'  from an unlimited supply of coins in set 'S'.
```py
def count(S, n, target):
    # Create a table to store the number of ways for each target amount
    dp = [0] * (target + 1)

    # There is one way to make a change of 0 (no coins)
    dp[0] = 1

    # Populate the dp table
    for i in range(0, n + 1):
        for j in range(S[i], target + 1):
            dp[j] += dp[j - S[i]]

    return dp[target]

if __name__ == '__main__':
    S = []
    n = int(input())
    target = int(input())
    for i in range(n):
        S.append(int(input()))
    ways = count(S, len(S) - 1, target)
    print('The total number of ways to get the desired change is', ways)
```
## Day 3 - Kadane's Algorithm
### Write a python program to find the maximum contiguous subarray.
```py
def maxSubArraySum(a, size):
    max_so_far = a[0]  # Initialize the maximum sum
    max_ending_here = a[0]  # Initialize the current subarray sum

    for i in range(1, size):
        max_ending_here = max(a[i], max_ending_here + a[i])
        max_so_far = max(max_so_far, max_ending_here)

    return max_so_far   
n=int(input())  
a =[] #[-2, -3, 4, -1, -2, 1, 5, -3]
for i in range(n):
    a.append(int(input()))
  
print("Maximum contiguous sum is", maxSubArraySum(a,n))
```
## Day 4 - Minimum Jump to Reach End Array
### Create a python program to find Minimum number of jumps to reach end  of the array using naive method(recursion)
```py
def minJumps(arr, l, h):
    if (h == l):
        return 0
    if (arr[l] == 0):
        return float('inf')
    min = float('inf')
    for i in range(l + 1, h + 1):
        if (i < l + arr[l] + 1):
            jumps = minJumps(arr, i, h)
            if (jumps != float('inf') and jumps + 1 < min):
                min = jumps + 1
    return min
arr = []
n = int(input())
for i in range(n):
    arr.append(int(input()))
print('Minimum number of jumps to reach','end is', minJumps(arr, 0, n-1))
```
