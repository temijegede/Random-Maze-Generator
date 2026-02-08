# 🧩 Maze Generator

![Python](https://img.shields.io/badge/python-3.x-blue.svg)
![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)
![Status](https://img.shields.io/badge/status-stable-brightgreen.svg)
![Made with NumPy](https://img.shields.io/badge/made%20with-numpy-orange.svg)

A Python-based maze generator using a **randomized depth-first search (DFS)** algorithm.  
Supports ASCII visualization, dead-end detection, maze braiding, and binary grid export.

---

## ✨ Features

- Randomized DFS maze generation
- ASCII-based maze rendering
- Binary matrix representation (`NumPy`)
- Dead-end detection
- Maze braiding with configurable probability
- Path plotting for algorithms & visualization

---

## Constraints and Notes
- Maze dimensions must be odd
- Minimum size is 3 x 3
- Default generation creates perfect mazes
- Braiding introduces loops
- Coordinate system uses (x, y) internally

## 📦 Requirements

- Python **3.x**
- NumPy

```bash
pip install numpy
```

---

## Maze Representation
The maze is stored internally in two formats:

Dictionary Grid
self.maze[(x, y)] → WALL / EMPTY

Binary Grid (NumPy)
1 → Wall, 0 → Empty

| Element            | Symbol |
| ------------------ | ------ |
| Wall               | `█`    |
| Empty Cell         | `' '`  |
| Generator Position | `@`    |
| Path               | `.`    |
| Invalid Path       | `E`    |


## 🚀 Quick Start
```Python
from Mazer import Maze

maze = Maze(21, 21) # Height and Width of maze must be odd
maze.buildMaze(1, 1)
maze.braidMaze(p=0.7)
maze.printMaze()
```
## Functions
### Maze Generation
```Python
buildMaze(x, y)
```
This function generates a perfect maze using a randomized DFS algorithm.
- Starting coordinates must be odd
- Automatically creates an entry and exit
- returns the exit coordinates

### 🖨️ Visualisation
```Python
printMaze()
printMaze(markX=1, markY=1) # Print with current position
```
This function prints the maze using the ASCII characters as defined in section (#maze-representation)

### Path Plotting
```Python
path = [(1,1),(1,3),(3,3),(3,5)]
plotPathinMaze(path)
```
Visualises the maze and overlays a path on the maze grid.

### Dead-End Detection
```Python
deadend()
```
Returns a list of all dead-end cells.
A dead end is defined as an empty cell with exactly one empty neighbor.

### Maze Braiding
```Python
braidMaze(p)
```
Removes dead ends to create loops.
p is the probability of braiding a deadend
| `p` Value | Behavior             |
| --------- | -------------------- |
| `0.0`     | No braiding          |
| `0.5`     | Partial braiding     |
| `1.0`     | Remove all dead ends |

---

## ❤️ Acknowledgements
Inspired by classic maze-generation algorithms and depth-first search techniques found in Mazes For Programmers by Jamis Buck, ISBN-10: 1680500554


