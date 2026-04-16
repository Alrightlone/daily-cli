# daily-cli

> **English** | **[中文](README_CN.md)**

Four minimal tools for your daily workflow:

- **`daily`** — open your morning routine websites in one command
- **`plan`** — task planner with carry-over, recurring rules, 7-day view, and streaks
- **`plan-ui`** — the planner as a clean desktop-like window (full + mini widget)
- **`journal`** — daily diary in markdown, one file per day

## Install

```bash
git clone https://github.com/Alrightlone/daily-cli.git
cd daily-cli
chmod +x daily plan plan-ui journal

# Add to PATH (zsh)
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

---

## `daily` — website opener

Opens your morning routine websites in Google Chrome, organized by category:

| Category | Sites |
|----------|-------|
| **social** | X, LinkedIn, GitHub |
| **scholar** | Google Scholar, Semantic Scholar |
| **papers** | HuggingFace Daily Papers |
| **ai** | ChatGPT, Claude, Gemini |

### Usage

```bash
daily              # Open all sites
daily social       # Open only X, LinkedIn, GitHub
daily scholar      # Open only Google Scholar, Semantic Scholar
daily papers       # Open only HuggingFace Daily Papers
daily ai           # Open only ChatGPT, Claude, Gemini
daily social ai    # Combine multiple categories
daily list         # List all URLs without opening
daily help         # Show help
```

---

## `plan` — daily task planner

A local task tracker for your daily plan. Each day is saved as a JSON file in `plans/`
(excluded from git — your plans stay private).

Tasks have four states:

| Icon | Status | Needs reason? |
|------|--------|---------------|
| ☐ | pending | — |
| ✓ | done | no |
| ◐ | half done | **yes** |
| ✗ | not done | **yes** |

### Usage

```bash
plan                             # Show today's plan
plan add "write draft"           # Add a new task
plan done 1                      # Mark task 1 as done
plan half 2                      # Mark task 2 as half done (prompts for reason)
plan skip 3                      # Mark task 3 as not done (prompts for reason)
plan edit 1 "new text"           # Rewrite task 1's text (fix typos)
plan rm 4                        # Remove task 4
plan clear                       # Remove all tasks for today (with confirmation)
plan week                        # Last 7 days at a glance + streak
plan recur add weekday "gym"     # Auto-add "gym" every weekday
plan recur list                  # List recurring rules
plan recur rm <id>               # Remove a recurring rule
plan edit                        # Open today's plan in $EDITOR (raw JSON)
plan show 2026-04-16             # Show a past day's plan
plan list                        # List all saved dates
plan help                        # Show help
```

**Automatic behaviors** (first `plan` each day):

- **Carry-over**: unfinished pending tasks from yesterday are brought into today, marked with `↪`
- **Recurring**: any matching rule (`daily` / `weekday` / `weekend` / `mon,wed,fri`) adds its task, marked with `↻`
- **Streak**: consecutive days with ≥ 1 completed task are counted and shown in the footer

### Example

```
  📅 2026-04-17  · Today

   1  ✓  Write paper draft
   2  ◐  Review PRs  · Only got through 2 of 3
   3  ✗  Gym  · Switched to indoor due to rain
   4  ☐  Read 2 HuggingFace daily papers

  ────────────────────────────────────────
  1/4 done · 1 half · 1 skipped · 1 pending
```

---

## `plan-ui` — desktop-style window

```bash
plan-ui              # full window
plan-ui mini         # compact widget, lives in a desktop corner
plan-ui both         # both windows on one server (live sync between them)
```

Launches a local server and opens the planner in a standalone Chrome window
(no tabs, no URL bar — feels like a native app). All changes sync with the same
`plans/*.json` files, so `plan`, `plan-ui`, and `plan-ui mini` all edit the same
data.

**Features**
- Click the status circle to pick ✓ done / ◐ half / ✗ skipped (modal asks for reason)
- Hover a task to edit or delete
- `A−` / `A+` buttons to adjust font size (remembered per window)
- Auto dark mode based on system preference
- Windows auto-refresh every 5s, so edits made elsewhere sync live
- Press `Esc` to close any modal or popover

The mini window is a compact widget you can park in a corner of your desktop
for at-a-glance reminders. Drag it by the background (not tasks or inputs).

Close the window to stop the server, or hit `Ctrl+C` in the terminal.

---

## `journal` — daily diary

```bash
journal                       # Edit today's entry in $EDITOR
journal yesterday             # Edit yesterday's entry
journal 2026-04-16            # Edit a specific date's entry
journal show 2026-04-16       # Print a past entry to the terminal
journal list                  # List all entries with a one-line preview
journal help                  # Show help
```

Each day is saved as a separate markdown file under `journal_entries/`
(gitignored). Fresh entries start with a prompt — replace it and write
whatever's on your mind. Uses `$EDITOR` (falls back to `nano`).

## Requirements

- macOS
- Google Chrome (for `daily` and `plan-ui`)
- Python 3 (for `plan`, `plan-ui`, `journal` — pre-installed on macOS)
- zsh (default shell on macOS)
- Internet connection on first UI load (Alpine.js loaded via CDN)

## License

MIT
