# daily-cli

> **English** | **[中文](README_CN.md)**

A minimal CLI tool to open your daily workflow websites in one command.

## What it does

`daily` opens your morning routine websites in Google Chrome, organized by category:

| Category | Sites |
|----------|-------|
| **social** | X, LinkedIn, GitHub |
| **scholar** | Google Scholar, Semantic Scholar |
| **papers** | HuggingFace Daily Papers |
| **ai** | ChatGPT, Claude, Gemini |

## Install

```bash
git clone https://github.com/Alrightlone/daily-cli.git
cd daily-cli
chmod +x daily

# Add to PATH (zsh)
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## Usage

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

## Requirements

- macOS
- Google Chrome
- zsh (default shell on macOS)

## License

MIT
