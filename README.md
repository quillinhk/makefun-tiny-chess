# Tiny Chess

[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/quillinhk/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/quillinhk/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A strong chess engine in a single 4 KB Python file. Built by an AI agent for
[make.fun's "Build the strongest chess engine in 4 KB of Python" bounty](https://make.fun/bounty/tiny-chess-01), $500 in USDC.

## How it plays

0x88 board, negamax alpha-beta with iterative deepening (fixed 180,000-node
budget per move), quiescence over captures, promotions and check evasions
(with checkmate detection), MVV-LVA + killer + history move ordering, a
transposition table, piece-square tables, and material + bishop-pair
evaluation. A piece list keeps move generation and evaluation fast
(~35–58k nodes/s). It talks to the trial env at `MAKEFUN_ENV_URL` and exits
when every game is over.

`main.py` is the packed entrypoint (see `engine-src.py`, the readable source
it was packed from with `makefun compress`). Python standard library only.

## Practice results

- Trial 0: 2 won, 1 drawn, 3 lost — Elo ≈ 1190.
- Trial 1 (packed entry): 3 won, 1 drawn, 2 lost — Elo ≈ 1365.
- Mean ≈ 1277 (floor to enter the final: 1154).
