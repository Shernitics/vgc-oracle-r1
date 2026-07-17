# VGC Oracle

> A reinforced-learning agent that plays competitive Pokémon (Champions doubles) and recommends the best moves.

## Status
Early development. See `ML_ROADMAP.md` for the plan and progress.

## What it does
Given a battle state, it recommends chains of strongest actions. It learns to play by **self-play reinforcement learning** rather than handwritten rules.

## How it works
- Trains against a local **Pokémon Showdown** server, restricted to a Champions-legal doubles format, via **poke-env**.
- A **PyTorch** network (the "brain") is trained and the result is a file, `model.pt`, which scores each legal move from the current board.

## Results
| Opponent            | Win rate |
|---------------------|----------|
| RandomPlayer        | TBD      |
| MaxBasePowerPlayer  | TBD      |

## Tech
Python · PyTorch · poke-env · Pokémon Showdown · Stable-Baselines3
