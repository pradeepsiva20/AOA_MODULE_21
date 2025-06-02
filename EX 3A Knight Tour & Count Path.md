# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight


## Algorithm
1. Start with a matrix representing the grid and initialize a 3D dynamic programming (DP) table to store results of subproblems.
2. Define a recursive function to calculate the number of paths to reach cell (m, n) with exact cost k using memoization to avoid recalculations.
3. At each step, move either from the top or from the left, and subtract the value of the current cell from the remaining cost k.
4. Use base conditions to return 1 if the top-left cell is reached and the cost is matched; otherwise, return 0.
5. Finally, return the computed value stored in the DP table as the number of valid paths that result in the target sum.
 

## Program:
```python
/*
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.
Developed by: PRADEEP S
Register Number: 212222100034
*/

R = 3
C = 3
MAX_K = 1000
def pathCountDPRecDP(mat, m, n, k):
    #############  Add your code #############
    if m < 0 or n < 0 or k < 0:
        return 0
    elif m == 0 and n == 0:
        return k == mat[m][n]
    if (dp[m][n][k] != -1):
        return dp[m][n][k]
    dp[m][n][k] = (pathCountDPRecDP(mat, m - 1, n, k - mat[m][n]) +
                   pathCountDPRecDP(mat, m, n - 1, k - mat[m][n]))
     
    return dp[m][n][k]
def pathCountDP(mat, k):
    return pathCountDPRecDP(mat, R - 1, C - 1, k)
k = 12
dp = [[ [-1 for col in range(MAX_K)]
            for col in range(C)]
            for row in range(R)]
mat = [[1, 2, 3],
       [4, 6, 5],
       [3, 2, 1]]
print(pathCountDP(mat, k))

```

## Output:

![image](https://github.com/user-attachments/assets/ecbc0a6e-9485-46ee-9f65-f077fcc52583)



## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
