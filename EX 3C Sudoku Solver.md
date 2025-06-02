
# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm
1. Start by scanning the Sudoku grid to find the first empty cell (represented by 0).
2. Try placing digits 1 to 9 in the empty cell and check if the number is safe to place (i.e., not repeated in its row, column, or 3×3 subgrid).
3. If the number is valid, place it and recursively try to fill in the rest of the grid.
4. If placing any number leads to a dead end, backtrack by resetting the cell and trying the next number. 
5. Repeat this process until the grid is completely filled, printing the result once a solution is found.
  

## Program:
```
/*
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: PRADEEP S
Register Number:212222100034
*/

board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0,9):
        for j in range(0,9):
            if board[i][j] == 0:
                for val in range(1,10):
                    if isPossible(board,i,j,val):
                        board[i][j] = val
                        solve()
                        board[i][j]=0
                return 
    printBoard(board)        
solve()
```

## Output:

![image](https://github.com/user-attachments/assets/3df54db1-3a25-4ec5-8fcf-2bc72cc6245c)



## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
