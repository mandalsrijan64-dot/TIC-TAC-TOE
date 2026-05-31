# Tic-Tac-Toe AI
## Tic-Tac-Toe Using JavaScript, HTML, and CSS – Description

Tic-Tac-Toe is a simple and interactive web-based game developed using HTML, CSS, and JavaScript. The game is designed for two players who take turns marking spaces in a 3×3 grid with the symbols "X" and "O". The objective is to place three of the same symbols consecutively in a row, column, or diagonal before the opponent does. This project is an excellent way to learn the fundamentals of front-end web development and game logic implementation.

HTML is used to create the structure of the game, including the game board, player information, status messages, and control buttons such as "Restart Game". CSS is responsible for the visual appearance of the game, providing an attractive layout, responsive design, animations, and styling for the grid cells. JavaScript handles the game functionality, including player turns, move validation, winner detection, score updates, and game reset operations.

The game begins with an empty 3×3 grid. Players click on a cell to place their symbol. JavaScript tracks each move and updates the board accordingly. After every turn, the program checks all possible winning combinations to determine if a player has won the game. If all cells are filled without a winner, the game declares a draw. The application then allows players to restart and play again.

Additional features can be incorporated to enhance the user experience, such as score tracking, sound effects, animations, highlighting the winning combination, dark mode support, and single-player mode against a computer opponent. More advanced versions can implement Artificial Intelligence using algorithms like Minimax to create an unbeatable computer player.

One of the major advantages of this project is its simplicity and educational value. It helps developers understand event handling, DOM manipulation, conditional logic, arrays, functions, and user interface design. Since the game runs entirely in a web browser, it is lightweight, platform-independent, and requires no additional software installation.

Overall, the Tic-Tac-Toe game using JavaScript, HTML, and CSS is a beginner-friendly project that combines programming logic with web design. It provides practical experience in developing interactive applications and serves as a strong foundation for creating more complex browser-based games and web applications in the future.

An unbeatable Tic-Tac-Toe AI built with vanilla HTML, CSS, and JavaScript.
Implements both **Minimax** and **Minimax with Alpha-Beta Pruning**.

## Project Structure

```
tictactoe-ai/
├── index.html          ← Main page
├── css/
│   └── style.css       ← All styles (dark theme)
├── js/
│   ├── game.js         ← Board state, win detection, rendering
│   ├── ai.js           ← Minimax & Alpha-Beta algorithms
│   └── main.js         ← Controller: ties everything together
└── README.md
```

## How to Run

### Option 1 — Live Server (Recommended)
1. Install the **Live Server** extension in VS Code
   (`ritwickdey.LiveServer`)
2. Right-click `index.html` → **Open with Live Server**
3. Browser opens automatically at `http://127.0.0.1:5500`

### Option 2 — Direct file open
Open `index.html` directly in any browser (no server needed —
this project uses no ES modules or fetch calls).

## How it Works

### Minimax
Recursively explores every possible game state.
The AI picks the move with the highest score assuming the human
always plays optimally.

| Outcome   | Score        |
|-----------|--------------|
| AI wins   | +10 − depth  |
| Human wins| −10 + depth  |
| Draw      | 0            |

Depth is subtracted/added so the AI prefers *faster* wins
and *longer* losses.

### Alpha-Beta Pruning
An optimisation of Minimax that skips branches that cannot
affect the final decision.

- `alpha` = best score the maximiser (AI) can guarantee
- `beta`  = best score the minimiser (human) can guarantee
- If `beta ≤ alpha` → prune the remaining siblings

Reduces complexity from **O(b^d)** to **O(b^(d/2))** in the
best case — roughly halving the search depth for the same cost.

## Difficulty Levels

| Level     | Behaviour                        |
|-----------|----------------------------------|
| Easy      | Picks a random empty cell        |
| Medium    | 60% optimal move, 40% random     |
| Unbeatable| Full Minimax — cannot be beaten  |

## Key Files Explained

### js/game.js
- `createBoard()` — returns a fresh 9-cell array
- `getEmptyCells(board)` — returns indices of empty cells
- `checkResult(board)` — detects win / draw / in-progress
- `renderBoard(board, winCells)` — updates the DOM

### js/ai.js
- `minimax(board, depth, isMaximising)` — plain minimax
- `minimaxAlphaBeta(board, depth, isMaximising, alpha, beta)` — pruned
- `getBestMove(board, algo)` — returns the best move index
- `getAiMove(board, algo, difficulty)` — applies difficulty logic

### js/main.js
- Handles click events, turn sequencing, score tracking
- Calls AI after a 150ms delay (so the human's move renders first)

OUTPUT:
