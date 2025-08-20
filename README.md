# ♔ JavaScript Chess Game

A fully functional chess game built with vanilla JavaScript, HTML, and CSS. Features complete chess piece movement logic, turn-based gameplay, and interactive piece highlighting.

## 📋 Table of Contents

- [Features](#features)
- [Game Rules](#game-rules)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Game Structure](#game-structure)
- [Core Components](#core-components)
- [Piece Movement Logic](#piece-movement-logic)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Complete Chess Gameplay**: All standard chess pieces with accurate movement patterns
- **Interactive UI**: Click to select pieces and view possible moves
- **Move Validation**: Proper chess rules enforcement
- **Turn-Based System**: Alternating white and black player turns
- **Piece Capture**: Full capture mechanics
- **Castling Support**: King-side castling for both colors
- **Visual Feedback**: Highlighted squares for possible moves
- **Animated Transitions**: Smooth piece movement animations

## 🎯 Game Rules

The game follows standard chess rules:

### Piece Movement
- **King**: One square in any direction (includes castling)
- **Queen**: Any number of squares horizontally, vertically, or diagonally
- **Rook**: Any number of squares horizontally or vertically
- **Bishop**: Any number of squares diagonally
- **Knight**: L-shaped moves (2+1 squares)
- **Pawn**: Forward one square, or two on first move; captures diagonally

### Special Rules
- **Castling**: King-side castling implemented for both players
- **Piece Capture**: Click on opponent pieces to capture
- **Turn System**: White moves first, then alternating turns
- **Move Validation**: Only legal moves are highlighted and allowed

## 🛠️ Tech Stack

- **JavaScript ES6+** - Game logic and DOM manipulation
- **HTML5** - Game board structure
- **CSS3** - Styling and animations
- **jQuery** - DOM manipulation and event handling
- **Unicode Chess Symbols** - Piece representations (♔♕♖♗♘♙)

## 🚀 Installation

1. **Clone or download the repository**
   ```bash
   git clone <your-repository-url>
   cd chess-game
   ```

2. **Ensure you have the required files**
   ```
   chess-game/
   ├── index.html
   ├── styles.css
   ├── chess.js (your game logic)
   └── README.md
   ```

3. **Open the game**
   - Open `index.html` in your web browser
   - No server setup required - runs locally

## 🏗️ Game Structure

### HTML Structure
The game expects an 8x8 grid with cells having IDs in the format `{column}_{row}`:
```html
<div class="gamecell" id="1_1"></div>
<div class="gamecell" id="1_2"></div>
<!-- ... continuing through 8_8 -->
```

### CSS Classes
- `.gamecell` - Individual chess squares
- `.green` - Highlighted possible moves
- `.shake-little` - Animation effect
- `.neongreen_txt` - Text highlighting
- `.turnhighlight` - Turn indicator animation

## 🔧 Core Components

### Main Object Structure
```javascript
let main = {
  variables: {
    turn: 'w',              // Current player turn
    selectedpiece: '',      // Currently selected piece ID
    highlighted: [],        // Array of highlighted squares
    pieces: {              // All piece objects
      // 32 chess pieces with properties:
      // - position: 'x_y' coordinates
      // - img: Unicode chess symbol
      // - captured: boolean
      // - moved: boolean (for castling/pawn logic)
      // - type: piece type identifier
    }
  },
  methods: {
    gamesetup(),           // Initialize board
    moveoptions(),         // Calculate valid moves
    options(),             // Filter valid coordinates
    w_options(),           // White piece line-of-sight
    b_options(),           // Black piece line-of-sight
    capture(),             // Handle piece capture
    move(),                // Execute piece movement
    endturn(),             // Switch player turns
    togglehighlight()      // Visual move indicators
  }
}
```

## 🎮 Piece Movement Logic

### Kings
- Standard one-square movement in all directions
- King-side castling when conditions are met:
  - King hasn't moved
  - Rook hasn't moved  
  - No pieces between king and rook

### Queens, Rooks, Bishops
- Line-of-sight movement using `w_options()`/`b_options()`
- Movement stops at first piece encountered
- Can capture opponent pieces
- Cannot jump over pieces

### Knights
- L-shaped movement pattern: 2+1 squares
- Can jump over other pieces
- 8 possible moves from any position

### Pawns
- Forward movement (white up, black down)
- Two squares on first move
- Diagonal capture only
- Special pawn logic in `options()` method

## 🎯 Usage

### Basic Gameplay
1. **Select a piece**: Click on any piece of your color
2. **View possible moves**: Green highlighted squares show valid moves
3. **Make a move**: Click on a highlighted square
4. **Capture pieces**: Click on opponent pieces within move range
5. **Turn indicator**: Display shows current player's turn

### Controls
- **Left Click**: Select pieces and make moves
- **Right Click**: Disabled (context menu prevented)

### Game Flow
```javascript
// Turn sequence
White moves → Black moves → White moves → ...

// Move validation
Click piece → Show options → Click target → Validate → Execute → End turn
```

## 🔍 Key Functions

### `gamesetup()`
Initializes the chess board by placing all pieces in starting positions.

### `moveoptions(selectedpiece)`
Calculates and highlights all valid moves for the selected piece based on chess rules.

### `options(startpoint, coordinates, piecetype)`
Filters coordinates to remove invalid moves (out of bounds, blocked by pieces, etc.).

### `w_options()` / `b_options()`
Implements line-of-sight movement for sliding pieces (queen, rook, bishop).

### `move()` / `capture()`
Executes piece movement and capture logic, updating board state.

### `endturn()`
Switches between white and black turns, resets selection state.

## 🐛 Known Limitations

- **Queen-side castling**: Not implemented
- **En passant**: Not implemented  
- **Pawn promotion**: Not implemented
- **Check/Checkmate detection**: Not implemented
- **Stalemate detection**: Not implemented
- **Move history**: Not tracked

## 🤝 Contributing

Contributions welcome! Areas for improvement:

### Priority Features
1. **Check/Checkmate Detection**
2. **Pawn Promotion**
3. **En Passant Capture**
4. **Queen-side Castling**
5. **Game State Persistence**

### Code Improvements
1. **Move Validation Enhancement**
2. **AI Opponent**
3. **Move History/Undo**
4. **Sound Effects**
5. **Responsive Design**

### Development Guidelines
- Follow existing code structure and naming conventions
- Test all piece movements thoroughly
- Ensure turn-based logic remains intact
- Add comments for complex chess rule implementations

## 📄 License

This project is open source. Feel free to use, modify, and distribute.

## 🏆 Acknowledgments

- Unicode Consortium for chess piece symbols
- jQuery team for DOM manipulation library
- Chess community for rule specifications

---

**Enjoy your game of chess! ♔♕♖♗♘♙**
