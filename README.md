# INFILTRADO — Operating Systems II Final Project (2019)

> Final project for the Operating Systems II course — UTU ESI Buceo, 2019.
> Authors: Gaston Benitez, Joaquin Rossi — 2BC

A text-based terminal game written in Bash that teaches Linux commands through an interactive spy narrative (in Spanish). Players log in, complete a tutorial, then choose between easy and hard story modes — all using real shell commands as answers.

---

## Gameplay

```
Login / Register
    └── Main Menu
            ├── Tutorial  (teaches mv, cd, cat, tac, grep, sed)
            └── Story Mode
                    ├── Easy Mode   — multiple choice, 5 questions, +15 pts each
                    └── Hard Mode   — free-form command input, 5 chapters, +10/-5 pts
```

### Commands taught

| Chapter | Command |
|---|---|
| 1 | `cd bases/TipoInfiltrado/NombreClave` |
| 2 | `cat Rerr.txt` |
| 3 | `tac Rerr.txt` (read backwards) |
| 4 | `grep -i overmon salir` |
| 5 | `sed 's/Pensilvania/Colombia/gi' datosvuelo` |

---

## How it works

- **Auth**: user accounts are directories under `Infiltrado/users/<username>/<password>/`
- **State**: bash variables track correct/wrong answers per chapter
- **Scoring**: hard mode = +10 per correct, -5 per wrong; easy mode = +15 per correct
- **Navigation**: `until` loops drive all menus; functions call each other for flow

---

## Running

```bash
bash infiltrado.sh
```

Requires: Linux or macOS (uses `clear`, `sleep`, ANSI colors, Unicode box-drawing).

---

## Files

| File | Description |
|---|---|
| `infiltrado.sh` | The entire game — single bash script, ~2400 lines |

---

## Tech Stack

- **Bash** — single-file script
- **ANSI escape codes** — terminal colors and formatting
- **Unicode** — box-drawing characters for UI frames
- **Linux filesystem** — used as a state machine for user auth
