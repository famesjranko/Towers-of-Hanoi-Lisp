# Lisp Towers of Hanoi Solver

A Lisp-based implementation of the classic Towers of Hanoi problem, featuring both breadth-first search (BFS) and A* search algorithms. This project explores state space search strategies, comparing their efficiency and performance.

## Project Overview

This project solves the Towers of Hanoi problem by representing states as lists and utilizing two search strategies: breadth-first search (BFS) and A* search with a heuristic. BFS explores the entire search space, while A* optimizes the search process using a custom heuristic. The goal is to compare the performance of these algorithms as the number of disks increases.

### Problem Description

- **Initial State:** Disks are stacked on peg A (smallest to largest), with Pegs B and C empty.
- **Goal State:** All disks must be moved to peg C, following the rule that no larger disk can be placed on top of a smaller one.

## Features

### Breadth-First Search (BFS) Function

The BFS function systematically explores all possible moves level by level. It starts with the initial state and explores all child nodes before moving on to deeper levels. This ensures that BFS will find the shortest solution but becomes inefficient with larger numbers of disks as it explores all possible paths exhaustively.

BFS expands every node, making it computationally expensive as the number of disks increases, compared to A* search, which optimizes by using heuristics to guide the search more intelligently.

- Explores all possible moves level by level.
- Efficient for small problem sizes but becomes slow as the number of disks increases.

### Heuristic Function in A* Search

The heuristic function used in A* search prioritizes moves that place larger disks in their correct positions first. This approach reduces the number of nodes visited and improves performance over BFS, particularly for larger problem sizes.

- Uses a heuristic to prioritize moves that are closer to the goal state.
- Significantly reduces the number of nodes visited and improves search depth and efficiency

## Performance Comparison

A comparison of BFS and A* search demonstrates the efficiency gains from using the heuristic in A* search, especially as the number of disks increases:

| n-discs | BFS Nodes | A* Nodes | BFS Depth | A* Depth |
|---------|-----------|----------|-----------|----------|
| 3       | 51        | 9        | 25        | 5        |
| 4       | 216       | 49       | 53        | 13       |
| 5       | 1351      | 117      | 286       | 18       |
| 6       | 7246      | 347      | 736       | 39       |
| 7       | 45453     | 981      | 4049      | 47       |
| 8       | 265964    | 2948     | 11403     | 81       |

## How to Run the Program

This project consists of three Lisp files:

1. **towers.lisp:** Implements the state space, problem definition, and move operations.
2. **bfs.lisp:** Implements the Breadth-First Search (BFS) algorithm.
3. **a-star.lisp:** Implements the A* search algorithm with a custom heuristic.

### Prerequisites

You will need **CLISP** to run the program.

### Breadth-First Search Test

1. **Start the CLISP interpreter:**
   ```bash
   $ clisp
   ```

2. **Run the BFS algorithm:**
   ```lisp
   (defun test-bfs ()
     (load "towers.lisp")
     (load "bfs.lisp")
     (reset-stats)
     (breadth-first-search *start-state* *operators*)
     *stats*)
   ```

3. **Execute the test:**
   ```lisp
   (test-bfs)
   ```

### A* Search Test

1. **Run the A* search algorithm:**
   ```lisp
   (defun test-a-star ()
     (load "towers.lisp")
     (load "a-star.lisp")
     (reset-stats)
     (a-star-search *start-state* *operators*)
     *stats*)
   ```

2. **Execute the test:**
   ```lisp
   (test-a-star)
   ```
