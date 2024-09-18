# Lisp: Towers of Hanoi Solution

A Lisp-based implementation of the Towers of Hanoi problem, demonstrating the effectiveness of best-first search over breadth-first search. This project includes a heuristic that drastically reduces both time and space complexity, enabling the solution of larger problem sizes.

## Problem Overview

The Towers of Hanoi puzzle involves moving a set of discs from one tower to another, following these rules:
1. Only one disc may be moved at a time.
2. A larger disc cannot be placed on a smaller disc.
3. All discs must end up in the final tower, preserving their order.

## Search Algorithms

### Breadth-First Search (BFS)
BFS explores all possible moves level by level, visiting a large number of nodes before finding the solution, leading to high time and space complexity.

### Best-First Search (BestFS)
BestFS uses a heuristic to prioritize moves that bring the state closer to the goal, significantly reducing the number of nodes visited and the depth of search required.

### Heuristic Explanation
The heuristic is based on:
1. **Order of Discs**: Measures how far the discs are from their correct order in the goal state.
2. **Length of Towers**: Gives preference to configurations where more discs are in the correct tower.

This approach minimizes the number of explored nodes and maximizes efficiency.

### Example of Improvement:
For 8 discs:
- **BFS** visited 265,964 nodes, with a max search depth of 11,403.
- **BestFS** visited only 2,948 nodes, with a max search depth of 81, improving performance by over 98%.

## Performance Data:

| **n-discs** | **BFS (n-nodes)** | **BestFS (n-nodes)** | **BFS (m-length)** | **BestFS (m-length)** |
|-------------|-------------------|----------------------|--------------------|-----------------------|
| 3           | 51                | 9                    | 25                 | 5                     |
| 4           | 216               | 49                   | 53                 | 13                    |
| 5           | 1,351             | 117                  | 286                | 18                    |
| 6           | 7,246             | 347                  | 736                | 39                    |
| 7           | 45,453            | 981                  | 4,049              | 47                    |
| 8           | 265,964           | 2,948                | 11,403             | 81                    |
| 9           | ---               | 8,637                | ---                | 125                   |
| 10          | ---               | 27,882               | ---                | 276                   |
| 11          | ---               | 83,006               | ---                | 453                   |

## How to Run the Program:

1. **Start the CLISP interpreter:**
   ```
   $ clisp
   ```

2. **Load the program:**
   ```lisp
   (load "towers-of-hanoi.lisp")
   ```

3. **Set the number of discs (optional):**
   ```lisp
   (setq *size* 5)
   ```

4. **Run the program:**
   ```lisp
   (solve)
   ```
