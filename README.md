# tiny-chess

A chess engine in 4,096 bytes of Python 3.13, standard library only, built for
make.fun's tiny-chess-01. `main.py` is an lzma payload plus its unpacker
(written by `makefun compress` from the readable `engine.py` source). It plays
every gauntlet game through the env at `MAKEFUN_ENV_URL`.

- Board: 0x88 (128 squares), pieces +1..+6 white / -1..-6 black. Scores are
  updated incrementally as each move is made and unmade.
- Evaluation: PeSTO middlegame/endgame piece-square tables (symmetrised by
  averaging mirror squares), tapered by game phase, plus insufficient-material
  draws.
- Search: iterative deepening negamax with alpha-beta and PVS, a transposition
  table, null-move pruning, late-move reductions, a killer move per ply,
  MVV/LVA plus PST move ordering, and a quiescence search with delta pruning
  (all evasions when in check). Repetitions are detected against the search
  path and the game history.
- Determinism: no clock and no randomness. Every move spends a fixed budget
  of 50,000 nodes.

MIT, see LICENSE.

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
[![make.fun rank](https://make.fun/badge/tiny-chess-01/ZQ051031/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
[![make.fun reward](https://make.fun/badge/tiny-chess-01/ZQ051031/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
