# Lisp Towers of Hanoi Solver

A Lisp-based implementation of the classic Towers of Hanoi problem, featuring both breadth-first search (BFS) and A* search algorithms. This project explores state space search strategies, comparing their efficiency and performance.

## Project Overview

This project solves the Towers of Hanoi problem by representing states as lists and utilizing two search strategies: breadth-first search (BFS) and A* search with a heuristic. BFS explores the entire search space, while A* optimizes the search process using a custom heuristic. The goal is to compare the performance of these algorithms as the number of disks increases.

### Problem Description

- **Initial State:** Disks are stacked on peg A (smallest to largest), with Pegs B and C empty.
- **Goal State:** All disks must be moved to peg C, following the rule that no larger disk can be placed on top of a smaller one.

### Search Strategies

#### Breadth-First Search (BFS)
- Explores all possible moves level by level.
- Efficient for small problem sizes but becomes computationally expensive with more disks.

#### A* Search with Heuristic
- Uses a heuristic to prioritize moves that place larger disks in their correct positions first.
- Reduces the number of nodes visited and improves search depth and efficiency over BFS.

## Performance Comparison

Here is a detailed comparison of BFS and A* (Best-First Search) across various problem sizes, showing the number of nodes visited, maximum length of the search, solution length, and maximum depth:

### Breadth-First Search Results

| *size* | Nodes visited | Max length | Soln Length | Max-depth |
|--------|----------------|------------|-------------|-----------|
| 3      | 51             | 25         | 7           | 7         |
| 4      | 216            | 53         | 15          | 15        |
| 5      | 1351           | 286        | 31          | 31        |
| 6      | 7246           | 736        | 63          | 63        |
| 7      | 45453          | 4049       | 127         | 127       |
| 8      | 265964         | 11403      | 255         | 255       |

### A* Search (Best-First Search) Results

| *size* | Nodes visited | Max length | Soln Length | Max-depth |
|--------|----------------|------------|-------------|-----------|
| 3      | 9              | 5          | 7           | 8         |
| 4      | 49             | 13         | 15          | 16        |
| 5      | 117            | 18         | 31          | 32        |
| 6      | 347            | 39         | 63          | 64        |
| 7      | 981            | 47         | 127         | 128       |
| 8      | 2948           | 81         | 255         | 258       |
| 9      | 8637           | 125        | 511         | 512       |
| 10     | 27882          | 276        | 1023        | 1026      |
| 11     | 83006          | 453        | 2047        | 2048      |

### Analysis

For the 8-disc problem, A* search drastically reduced the number of nodes visited (from 265,964 for BFS to 2,948 for A*) and the maximum search depth (from 11,403 to 81). These improvements reflect a **98.89% reduction** in nodes visited and **99.29% reduction** in search depth, making A* search significantly more efficient for larger problem sizes.

---

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
