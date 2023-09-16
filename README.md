# AI-tictactoe

There are two main files in this project: runner.py and tictactoe.py. tictactoe.py contains all of the logic for playing the game, and for making optimal moves. runner.py contains all of the code to run the graphical interface for the game. Let’s open up tictactoe.py to get an understanding for what’s provided. First, we define three variables: X, O, and EMPTY, to represent possible moves of the board.

The function initial_state returns the starting state of the board.

The player function takes a board state as input, and returns which player’s turn it is (either X or O). 

  In the initial game state, X gets the first move. Subsequently, the player alternates with each additional move.
  Any return value is acceptable if a terminal board is provided as input (i.e., the game is already over).

The actions function returns a set of all of the possible actions that can be taken on a given board.

  Each action is represented as a tuple (i, j) where i corresponds to the row of the move (0, 1, or 2) and j corresponds to which cell in the row corresponds to the move (also 0, 1, or 2).
  Possible moves are any cells on the board that do not already have an X or an O in them.
  Any return value is acceptable if a terminal board is provided as input.

The result function takes a board and an action as input, and return a new board state, without modifying the original board. 

  The returned board state is the board that would result from taking the original input board, and letting the player whose turn it is make their move at the cell indicated by the input     action.
  Importantly, the original board is left unmodified: since Minimax ultimately require considering many different board states during its computation. This means that simply updating a       cell in board itself is not a correct implementation of the result function. that's why I made a deep copy of the board first before making any changes.

The winner function accepts a board as input, and returns the winner of the board if there is one.

  If the X player has won the game, the function will return X. If the O player has won the game, the function will return O.
  One can win the game with three of their moves in a row horizontally, vertically, or diagonally.
  no board will ever have both players with three-in-a-row, since that would be an invalid board state.
  If there is no winner of the game (either because the game is in progress, or because it ended in a tie), the function will return None.

The terminal function accepts a board as input, and returns a boolean value indicating whether the game is over.

  If the game is over, either because someone has won the game or because all cells have been filled without anyone winning, the function return True.
  Otherwise, the function return False if the game is still in progress.

The utility function accepts a terminal board as input and outputs the utility of the board.

  If X has won the game, the utility is 1. If O has won the game, the utility is -1. If the game has ended in a tie, the utility is 0.
  Utility will only be called on a board if terminal(board) is True.

The minimax function takes a board as input, and returns the optimal move for the player to move on that board.

  The move returned is the optimal action (i, j) that is one of the allowable actions on the board. If multiple moves are equally optimal, any of those moves is acceptable.
  If the board is a terminal board, the minimax function will return None.

