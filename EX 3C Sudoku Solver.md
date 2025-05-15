# EX 3C Sudoku Solver
## DATE:25.03.2025
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.

## Algorithm:
```
1.Define a helper function isPossible(row, col, val):
  Check if placing val at position (row, col) is valid
  Ensure val does not exist in the same row.
  Ensure val does not exist in the same column
  Ensure val does not exist in the 3×3 subgrid that contains (row, col).
2. Find the next empty cell isEmpty():
    Scan the board row by row.
    Return the coordinates (row, col) of the first empty cell (0).
    If no empty cell is found, the board is solved.
    Define the recursive solver solve():
    If there is no empty cell, the puzzle is solved — print the board.
Otherwise:
    Try digits from 1 to 9 in the empty cell.
    For each digit:
         If it is valid according to isPossible(...), place it on the board.
         Recur to solve the next empty cell.
         If recursion returns True, puzzle is solved — exit.
         If not, backtrack by resetting the cell to 0.
         If no digit fits, return False.
3.Main Execution:
   Call solve() to begin solving the board.
   It prints the board when solved.
```
## Program:
```

Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: SUROTHAAMAN R
Register Number:  212222103003
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

def printBoard():
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(row, col, val):
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
#####################  Add your code here #########################
def isEmpty():
    for r in range(9):
        for c in range(9):
            if board[r][c] == 0:
                return r, c
    return None


def solve():
    #####################  Add your code here #########################
    empty = isEmpty()
    if empty is None:
        printBoard()
        return True

    row, col = empty
    for guess in range(1, 10):
        if isPossible(row, col, guess):
            board[row][col] = guess
            if solve():
                return True
            board[row][col] = 0
    return False
solve()

```

## Output:
![Screenshot 2025-04-29 230511](https://github.com/user-attachments/assets/6f28bf86-8bc0-469b-9692-391b0afbe5f6)

## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
