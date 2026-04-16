# daily-cli

> **English** | **[中文](README_CN.md)**

Two minimal CLI tools for your daily workflow:

- **`daily`** — open your morning routine websites in one command
- **`plan`** — manage today's tasks from the terminal, saved locally

## Install

```bash
git clone https://github.com/Alrightlone/daily-cli.git
cd daily-cli
chmod +x daily plan

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
plan                       # Show today's plan
plan add "write draft"     # Add a new task
plan done 1                # Mark task 1 as done
plan half 2                # Mark task 2 as half done (prompts for reason)
plan skip 3                # Mark task 3 as not done (prompts for reason)
plan rm 4                  # Remove task 4
plan edit                  # Open today's plan in $EDITOR (raw JSON)
plan show 2026-04-16       # Show a past day's plan
plan list                  # List all saved dates
plan help                  # Show help
```

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

## Requirements

- macOS
- Google Chrome (for `daily`)
- Python 3 (for `plan`, pre-installed on macOS)
- zsh (default shell on macOS)

## License

MIT
