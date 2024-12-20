
# Connect Four Game: Documentation

## Overview
This implementation is a Python-based version of the Connect Four game, where a human player competes against an AI player. The AI uses the Minimax algorithm with alpha-beta pruning to make decisions.

---

## How to Play
1. The game board is a 6x7 grid where players take turns dropping pieces into one of the 7 columns.
2. Player 1 (human) uses `1` as their piece, while the AI uses `2`.
3. To make a move, Player 1 enters a column number (0-6) where they want to drop their piece.
4. The AI will automatically decide its move based on the current state of the board.
5. The first player to align four of their pieces horizontally, vertically, or diagonally wins the game.

---

## Code Structure

### Constants
- **ROW_COUNT**: Number of rows in the board (6).
- **COLUMN_COUNT**: Number of columns in the board (7).
- **PLAYER**: Identifier for the human player.
- **AI**: Identifier for the AI player.
- **EMPTY**: Represents an empty cell in the board.
- **PLAYER_PIECE**: The piece for the human player.
- **AI_PIECE**: The piece for the AI player.
- **WINDOW_LENGTH**: Number of pieces needed to win (4).

### Functions

#### `create_board()`
- **Purpose**: Initializes the game board as a 6x7 grid filled with zeros (empty cells).
- **Returns**: A 2D NumPy array representing the game board.

#### `drop_piece(board, row, col, piece)`
- **Purpose**: Places a piece on the board at the specified row and column.
- **Parameters**:
  - `board`: The game board.
  - `row`: The row index.
  - `col`: The column index.
  - `piece`: The player's piece (1 or 2).

#### `is_valid_location(board, col)`
- **Purpose**: Checks if a column has space for a piece.
- **Returns**: `True` if the column is not full, `False` otherwise.

#### `get_next_open_row(board, col)`
- **Purpose**: Finds the first available row in a column.
- **Returns**: The row index.

#### `print_board(board)`
- **Purpose**: Prints the game board, flipping it vertically for a proper view.

#### `winning_move(board, piece)`
- **Purpose**: Checks if a player has won the game.
- **Returns**: `True` if the player has won, `False` otherwise.

#### `evaluate_window(window, piece)`
- **Purpose**: Scores a subset (window) of the board based on potential winning conditions.
- **Returns**: A score for the window.

#### `score_position(board, piece)`
- **Purpose**: Calculates the overall score for the current board state.
- **Returns**: A numerical score.

#### `is_terminal_node(board)`
- **Purpose**: Checks if the game has reached a terminal state (win or draw).
- **Returns**: `True` if the game is over, `False` otherwise.

#### `minimax(board, depth, alpha, beta, maximizingPlayer)`
- **Purpose**: Implements the Minimax algorithm with alpha-beta pruning for the AI's decision-making.
- **Parameters**:
  - `board`: Current state of the game board.
  - `depth`: Search depth.
  - `alpha`: Alpha value for pruning.
  - `beta`: Beta value for pruning.
  - `maximizingPlayer`: `True` if it's the AI's turn, `False` otherwise.
- **Returns**: The column and score of the best move.

#### `get_valid_locations(board)`
- **Purpose**: Lists all columns where a piece can be dropped.
- **Returns**: A list of valid column indices.

#### `pick_best_move(board, piece)`
- **Purpose**: Picks the best move based on the current board score (alternative to Minimax).
- **Returns**: The best column index.

---

## Game Execution
1. The game board is created using `create_board()`.
2. The players take turns, starting with a random choice of PLAYER or AI.
3. After each move:
   - The board is updated using `drop_piece()`.
   - A check is performed using `winning_move()` to determine if the game has ended.
4. The AI's moves are determined using the `minimax()` algorithm.
5. The game ends when a player wins or the board is full.

---

## Example Run

```
[[0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0.]]
Player 1 Make your Selection (0-6):
```

---

## Notes
- The AI's difficulty can be adjusted by modifying the `depth` parameter in the `minimax()` function.
- The board is displayed with the top row at the bottom for visual clarity.
