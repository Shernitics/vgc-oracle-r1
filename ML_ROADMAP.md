# ML Roadmap 

**Goal:** a reinforcement-learning agent that plays competitive Pokémon (Champions doubles), trained by self-play, and can recommend moves from a board state.

## Taget & Stack
- **Game:** Pokémon Champions (doubles), approximated via a restricted custom **Showdown** doubles format (Champions-legal roster/items) on a local server.
- **Stack:** Python · PyTorch · poke-env · Pokémon Showdown · Stable-Baselines3

---

## Phase 1 - poke-env + Showdown running
- [ ] Get two scripted bots (RandomPlayer, MaxBasePowerPlayer) to battle locally

## Phase 2 - Data & meta teams
- [ ] Pick the target format/roster (Showdown-legal, meta-relevant)
- [ ] Pull usage stats → identify meta mons + common sets
- [ ] Build a pool of **meta teams** as Showdown team exports
- [ ] Set those teams as opponents in a battle

## Phase 3 - Simulate at volume
- [ ] Run N battles; scripted bots vs meta teams
- [ ] Wrap it so I can measure win-rate for any player

## Phase 4 - Grow PyTorch (the ML, incremental)
- [ ] `encode.py` - battle -> fixed vector (start minimal, expand)
- [ ] `model.py` - small net
- [ ] `env.py` - reset/step + reward (+1 win / -1 loss)
- [ ] `train.py` - PPO loop -> `models/model.pt`
- [ ] `evaluate.py` - win-rate vs RandomPlayer
- [ ] beats RandomPlayer
- [ ] beats MaxBasePowerPlayer

## Phase 5 - Strengthen & Plan
- [ ] History-aware net -> uses past events + infers hidden info
- [ ] Reward shaping/tuning; vary opponent teams (avoid overfitting)
- [ ] Self-play (opponent = copy of current bot)
- [ ] MCTS on top of the net -> explicit forward planning

---

## Decision-making note
Not greedy - RL optimizes end-of-game reward, so state -> action accounts for multi-turn chains.

## References — pull ONLY when stuck
- Training "runs but won't learn" → [3B1B gradient descent](https://www.youtube.com/watch?v=IHZwWFHWa-w) · [HF Deep RL course](https://huggingface.co/learn/deep-rl-course/unit0/introduction)
- PyTorch mechanics → [PyTorch Basics](https://pytorch.org/tutorials/beginner/basics/intro.html)
- poke-env → [Getting Started](https://poke-env.readthedocs.io/en/stable/getting_started.html) · [env module](https://poke-env.readthedocs.io/en/stable/modules/env.html)
- Damage/validation → [Showdown calc](https://calc.pokemonshowdown.com/)
