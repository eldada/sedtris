# Sedtris

A fully functional Tetris clone written almost entirely in **sed** — the Unix stream editor. A small bash wrapper handles keyboard input and timing, while all game logic (piece spawning, rotation, movement, line clearing, scoring, and rendering) lives in a single sed script.

## Screenshot

```
+----------+
|          |   Next:
|          |    OO
|    OO    |    OO
|    OO    |
|          |   Score: 4
|          |
|          |
|          |  "w" or up - rotate
|          |  "a" or left - left
|          |  "d" or right - right
|  XX      |  "s" or down - one step down
|  XXXX    |  "z" or space - drop down
+----------+
```

## Requirements

- **bash**
- **sed** (GNU sed or compatible)
- A terminal emulator with ANSI color support

## How to Play

Clone the repository and run the game:

```bash
git clone https://github.com/eldada/sedtris.git
cd sedtris
./start.sh
```

Make sure the script is executable:

```bash
chmod +x start.sh
```

### Controls

| Key              | Action          |
|------------------|-----------------|
| `w` or `↑`       | Rotate piece    |
| `a` or `←`       | Move left       |
| `d` or `→`       | Move right      |
| `s` or `↓`       | Move down one step |
| `z` or `Space`   | Hard drop       |

## How It Works

The project consists of two files:

- **`sedtris.sed`** — The game engine. All Tetris logic is implemented as sed substitution commands: the board state, tetromino definitions, rotation, collision detection, line clearing, scoring, and ANSI-colored terminal rendering.
- **`start.sh`** — A bash wrapper that reads keyboard input (including arrow keys), auto-advances the game every second, and pipes everything into sed.

The board and pieces are encoded as compact strings using letter-based coordinates. Each game tick, sed processes the input, updates the board state, and prints a fresh frame with ANSI escape codes for colored blocks.

### Disabling Colors

To run without colors, uncomment line 336 in `sedtris.sed`:

```sed
s/\[\([0-9]*;\)*[0-9]*m//g
```

## Credits

Created by **Julia Jomantaite** (2008), based on [`playsed.sh`](http://sed.sf.net/grabbag/scripts/playsed.sh.txt) by Aurelio Marinho Jargas.
