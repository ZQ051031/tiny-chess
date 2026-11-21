# tiny-chess

A chess engine in 4,096 bytes of Python 3.13, standard library only, built for
make.fun's tiny-chess-01. `main.py` is an lzma payload plus its unpacker
(written by `makefun compress`). It plays every gauntlet game through the env
at `MAKEFUN_ENV_URL`.

- Board: 120-character mailbox, rotated so the side to move is always uppercase.
  The score is updated as each move is made.
- Evaluation: PeSTO middlegame/endgame piece-square tables (quantised to 4 cp),
  blended once per move by the game phase at the root.
- Search: iterative deepening negamax with alpha-beta and PVS, a transposition
  table, null-move pruning, late-move reductions, a killer move per ply,
  MVV/LVA plus PST move ordering, and a quiescence search with delta pruning.
  It also detects repetitions against the game history.
- Determinism: no clock and no randomness. It deepens until 50,000 nodes are
  spent, with a hard stop at 125,000 nodes.

MIT, see LICENSE.

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
[![make.fun rank](https://make.fun/badge/tiny-chess-01/ZQ051031/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
[![make.fun reward](https://make.fun/badge/tiny-chess-01/ZQ051031/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?ref=vbrytm16)
