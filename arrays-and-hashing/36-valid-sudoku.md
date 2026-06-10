---
tags:
  - leetcode
  - neetcode150
time_elapsed: 10
difficulty: easy
category: arrays-and-hashing
needed_help: false
link: https://leetcode.com/problems/valid-sudoku/
---

# 36. Valid Sudoku

## Notes
<small><i>Intuition and thought process in solving the question.</i></small>

I was already familiar with the brute force way on how to do this. This is definitely not the optimal solution. I basically had a helper function that checked a valid row. Then I transformed the sudoku board into 3 areas. One is the standard row check. The other is turning the columns into rows and then third is turning the 3x3 boxes into rows. Then I just fed it into the helper function. 

This solution is $O(n^2)$ time complexity.
## Code
<small><i>The solution.</i></small>

```python
class Solution:

	def isValidSudoku(self, board: List[List[str]]) -> bool:
		# Figure out if a sudoku board is valid or not
		first_row = board[0]
		print(first_row)
		print(self.is_valid_row(first_row))
		
		# My first thought process would be to have 3 different functions
		# My first naive approach
		# - first pass, go through each row and check valid
		# for rows
		for row in board:
			if not self.is_valid_row(row):
				return False

  
		# - second pass, go through each column and check valid
		# for columns
		column_board = []
		for col_i in range(len(board[0])):
			column = []
			for row_i in range(len(board)):
				item = board[row_i][col_i]
				column.append(item)
				
			if not self.is_valid_row(column):
				return False

  

		# - third pass, go through every 3x3 box and check valid

		map = {}
		for row_i in range(len(board)):
			for col_i in range(len(board[0])):
			
				row_coord = math.floor(row_i / 3)
				col_coord = math.floor(col_i / 3)
				coords = (row_coord, col_coord)
				
				if coords not in map:
					map[coords] = []
					map[coords].append(board[row_i][col_i])
					
		for box in map.values():
			if not self.is_valid_row(box):
				return False
		return True

  

	def is_valid_row(self, row: List[str]) -> bool:
		"""
		Checks to see if a row is valid.
		This means that all distinct numbers 1-9 are in there
		with no duplicates.
		"""
		num_holder = set()
		for num in row:
			if (num.isnumeric()):
				if (num not in num_holder):
					num_holder.add(num)
				else:
					return False
		return True
```

---
## Problem Statement
<small><i>The problem to solve.</i></small>