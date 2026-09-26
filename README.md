# Skirmish at Crane Reach agent

Edit `agent.py` to build one unit's behavior for Skirmish at Crane Reach. Every unit on a side runs a separate instance of the same `Agent` class, so they do not share state or variables. `sandbox/` is provided code: do not edit it.

Start with the [Getting Started guide](https://vox-deorum.github.io/game-sandbox/students/getting-started/). Then run these commands from this folder as you work:

```console
python -m sandbox play   # command a side yourself in your browser
python -m sandbox watch  # watch your agent take on Naive
python -m sandbox test   # run the provided checks
python -m sandbox eval   # compare your agent with Naive
```

**Naive** is a simple built-in opponent. It holds the other side in `watch` and `eval`, and `eval` reports your side's average score over repeatable matches. The [`environment.md`](environment.md) guide explains rivals, presets, and the other command options.

## Files you will use

| Path | Purpose |
| --- | --- |
| `agent.py` | Your `Agent` implementation and the first TODO locations. |
| `environment.md` | Crane rules, starter walkthrough, helpers, observations, and settings. |
| `manifest.json` | Names the agent class for a submission. |
| `season.json` | Optional local season settings downloaded from My Submissions. |
| `tests/` | Checks your submission should pass. |
| `sandbox/` | Local game, commands, helper package, and observation types. Do not edit it. |
| `requirements.txt` | Exact Python package versions used by the server. |
| `requirements-dev.txt` | Test dependencies. |
| `.env.example` | Example local LLM settings. |

The starter returns Crane orders with `action.move()` and `action.stay()` from `sandbox.crane`. Its `act(observation)` receives the current observation and action mask. Before changing the strategy, read [`environment.md`](environment.md). It starts with a small archer improvement you can copy, then explains when an order is legal.

Leave `sandbox/`, `requirements.in`, and `requirements.txt` unchanged. The pinned packages match the server. Ask your instructor before adding a package.

When your agent is ready, follow the shared [submitting guide](https://vox-deorum.github.io/game-sandbox/students/submitting/). For the optional `learn` and `chat` hooks, see the shared [agent interface](https://vox-deorum.github.io/game-sandbox/students/agent-interface/). Crane messaging begins in Season 3.

## Optional LLM API

If your instructor enables model calls, follow [Using the LLM API](llm.md). Copy `.env.example` to `.env`, add the endpoint and key, and never commit either secret.

Test the connection with:

```console
python -m sandbox llm
```
## Design Goal
Season 2: The goal this season was to make the archers fall back more efficiently, the cavalry braver, and have them all navigate the new terrain. Along with that, I added a utility function to better calculate risk-taking and decision-making.


## Reflection
Season 2: I worked through and tested the different choices of the characters, individually and together. I revised the cavalry based on the feedback; as though its week, it has good damage dealing. I considered utility methods alongside what risks and fallback strategies I wanted the archer and cavalry to make. I did not feel the need to change the footman. I also had it add a pathfinding tool to navigate the new terrain, but it got very complicated very quickly. I will need more testing to know why my numbers are still low.

## AI Use Disclosure and Reflection
I used Claude Code in VS Code. It coded all of this based on my pseudocode and instructions. I verified each set of code it wrote before approving it, reverted and asked for changes as needed, tested by watching and eval, and discussed my ideas for solutions before committing to one. I did not write any code directly, but read through it to check it. I had it set to ask for approval before committing anything, and that worked especially during testing and understanding what code was being changed. One big challenge was keeping it in check as it quickly started getting more complicated, and it even did testing before bug fixes without my approval. A lot was done that I don't understand, so I will ask it to go slower for me next time. 
