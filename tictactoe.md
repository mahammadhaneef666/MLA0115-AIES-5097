def print\_board(board): for row in board: print(" | ".join(row)) print("-" \* 5) def check\_winner(board, player):

for row in board: ![](Aspose.Words.5976d077-552a-4fcc-9ad8-0b8d8ac9034d.001.png)

`    `if all(cell == player for cell in row): 

`        `return True 

for col in range(3): 

`    `if all(board[row][col] == player for row in range(3)):         return True 

if all(board[i][i] == player for i in range(3)) or all(board[i][2 - i] == player for i in range(3)): 

`    `return True 

return False

def is\_board\_full(board): return all(cell != ' ' for row in board for cell in row) def tic\_tac\_toe(): board = [[' ' for \_ in range(3)] for \_ in range(3)] current\_player

= 'X'

while True: ![](Aspose.Words.5976d077-552a-4fcc-9ad8-0b8d8ac9034d.002.png)

`    `print\_board(board) 

row = int(input(f"Player {current\_player}, enter the row (0, 1, or 2): ")) col = int(input(f"Player {current\_player}, enter the column (0, 1, or 2): ")) 

`    `if board[row][col] != ' ': 

`        `print("Cell already occupied. Try again.")         continue 

board[row][col] = current\_player 

`    `if check\_winner(board, current\_player): 

`        `print\_board(board) 

`        `print(f"Player {current\_player} wins!")         break 

`    `elif is\_board\_full(board): 

`        `print\_board(board) 

`        `print("It's a tie!") 

`        `break 

`    `current\_player = 'O' if current\_player == 'X' else 'X' if **name** == "**main**": tic\_tac\_toe()
**output**
![image](https://github.com/user-attachments/assets/c8df22a1-4527-49b1-9418-b4ae36c7caff)
