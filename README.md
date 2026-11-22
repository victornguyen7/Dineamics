# Dineamics · Worcester

**A what-if simulator for the Worcester Dining Commons at UMass Amherst** (HackUMass 2026).
It simulates dinner night after night on the real menu, student by student, so a kitchen manager can test a decision (smaller batches, an extra server, a new dish, a busier night) before trying it on real students, and get a cook sheet with honest ranges and a "better / worse / can't tell" verdict.

## What's inside
- **Simulation:** watch a simulated night in a 3D hall, try a change, compare it with tonight's plan.
- **What-If Lab:** tune batches, staffing, crowd and menu (or ask in plain English); **Optimize** searches kitchen plans; **Plausible worlds** tests a plan when our guesses are off.
- **Kitchen plan:** tonight's numbers, arrivals, production plan, staffing, leftovers.
- **Insights:** waste for the coming nights and the recorded past; **Similar nights** finds past nights like tonight.
- **Ask Sam:** a Gemini planning agent that tests up to 5 ideas, answers questions from the recorded history, and hands back a plan.

Built with **Gemini** (function calling, Sam), **Tiger Data** (time series, pgvector search, forecast ledger), **Vultr** (hosting and a temporary server fleet for big searches) and a **GoDaddy Registry** domain. Works on desktop, iPad (portrait) and phone.

> The recorded waste history is **synthetic** until UMass Dining shares real exports. The menu is real.

## Quick start
```bash
cd web && npm install && npm run dev        # the app on http://localhost:5173, works offline from the demo bundle

# full setup: engine + API (Python ≥ 3.13, uv) in a second terminal
cd engine && uv sync && cd .. && make server   # API on http://127.0.0.1:8000, then `make web`
```

Command line: `cd engine && uv run dcsim run --date 2026-11-13` (30 nights) · `uv run dcsim compare --preset smaller_batches` · `uv run dcsim agent "cut waste 20% without any vegetarian dish running out"`

## Repo
| Folder | What |
| --- | --- |
| `engine/` | Python simulation engine, FastAPI server, `dcsim` CLI, Sam, Tiger and Vultr code |
| `web/` | React app (Vite), with the precomputed demo bundle in `web/public/cache` |
| `data/` | Real menus and Worcester inputs; synthetic recorded history |
| `deploy/` | Vultr server setup and the fleet runbook |
| `docs/` | Everything else |

## Docs
- **[Developer guide](docs/GUIDE.md):** setup, how it works, repo map, tasks, configuration, testing, troubleshooting
- [Status](docs/STATUS.md) · [Engine](docs/ENGINE.md) · [Tiger Data](docs/TIGER.md) · [Sponsors](docs/SPONSORS.md) · [Deploy](deploy/README.md) · [Pitch](docs/PITCH.md)
