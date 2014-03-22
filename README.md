class tictactoegame:
	def __init__(self, t):
			self.board=[[0,0,0], [0,0,0], [0,0,0]]
			self.turn=t
	def canPlacePiece(self, x, y):
		if self.board[x][y] == 0:
			return True
		else:
			return False
	def place_piece(self,x,y):
		if self.canPlacePiece(x, y) == True:
			self.board[x][y] = self.turn
			self.next_turn()
			
			
	def print_board(self):
		for x in range(0,3):
			output = ""
			for y in range(0,3):
				if self.board[x][y] == 0:
					output = output +  " "
				elif self.board[x][y] == 1:
					output = output + "X"
				elif self.board[x][y] == 2:
					output = output + "O"
				if y < 2:
					output = output + "|"
			print output
			if x < 2:
				print "-|-|-"
		 
	def has_won(self):
		for r in range(3):
			if self.board[r][0] != 0 and self.board[r][0] == self.board[r][1] == self.board[r][2]:
				return self.board[r][0]
		for c in range(3):
			if self.board[0][c] != 0 and self.board[0][c] == self.board[1][c] == self.board[2][c]:
				return self.board[0][c]
		if self.board[0][0] != 0 and self.board[0][0] == self.board[1][1] == self.board[2][2]:
			return self.board[0][0]
		if self.board[0][2] != 0 and self.board[0][2] == self.board[1][2] == self.board[2][0]:
			return self.board[0][2]
		return 0
	def next_turn(self):
		if self.turn == 1:
			self.turn = 2
		else:
			self.turn = 1

	def computer_move(self):
		#computer makes a move pick best move place piece
		#then the human plays


game = tictactoegame(1)

while game.has_won() == 0:
	game.print_board()
	game.place_piece(input("Enter a row:"), input("Enter a column: "))

	



