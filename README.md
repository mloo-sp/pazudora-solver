[![PyPI version](https://badge.fury.io/py/pazudorasolver.svg)](https://badge.fury.io/py/pazudorasolver)
[![Supported Python Versions](https://img.shields.io/pypi/pyversions/pazudorasolver.svg)](https://pypi.python.org/pypi/pazudorasolver/)
[![Build Status](https://travis-ci.org/ethanlu/pazudora-solver.svg?branch=master)](https://travis-ci.org/ethanlu/pazudora-solver)
[![Requirements Status](https://requires.io/github/ethanlu/pazudora-solver/requirements.svg?branch=master)](https://requires.io/github/ethanlu/pazudora-solver/requirements/?branch=master)
[![Codacy Badge](https://api.codacy.com/project/badge/grade/78cdfdafa28f4475a3dea086c3dd006d)](https://www.codacy.com/app/ethanoks/pazudora-solver)
[![Coverage Status](https://coveralls.io/repos/github/ethanlu/pazudora-solver/badge.svg?branch=master)](https://coveralls.io/github/ethanlu/pazudora-solver?branch=master)

Pazudora Solver
=====

Python-based solver for the [Puzzles and Dragons mobile game](http://www.gunghoonline.com/games/puzzle-dragons/).
Inspired by the [Javascript version](https://github.com/alexknutson/Combo.Tips) on [Combo.tips](http://combo.tips/)

### Example
```python
from pazudorasolver.board import Board
from pazudorasolver.piece import Fire, Wood, Water, Dark, Light, Heart, Poison, Jammer, Unknown
from pazudorasolver.heuristics.greedy_dfs import GreedyDfs
from pazudorasolver.heuristics.pruned_bfs import PrunedBfs

weights = {Fire.symbol: 2.0,
           Wood.symbol: 2.0,
           Water.symbol: 2.0,
           Dark.symbol: 2.0,
           Light.symbol: 2.0,
           Heart.symbol: 1.0,
           Poison.symbol: 0.5,
           Jammer.symbol: 0.5,
           Unknown.symbol: 0.0}

board = Board.create_randomized_board(5, 6)
matches = board.get_matches()

print board
print matches

solver1 = GreedyDfs(weights)
solution = solver1.solve(board, 50)

print solution

solver2 = PrunedBfs(weights)
solution = solver2.solve(board, 50)

print solution
```

## TODO
- Improve score calculation (TPA, Row-clear, N-match, etc.)
- Additional heuristics for solving board