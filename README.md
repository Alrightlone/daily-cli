# daily-cli

> **[English](#english)** | **[中文](#中文)**

---

## English

A minimal CLI tool to open your daily workflow websites in one command.

### What it does

`daily` opens your morning routine websites in Google Chrome, organized by category:

| Category | Sites |
|----------|-------|
| **social** | X, LinkedIn, GitHub |
| **scholar** | Google Scholar, Semantic Scholar |
| **papers** | HuggingFace Daily Papers |
| **ai** | ChatGPT, Claude, Gemini |

### Install

```bash
git clone https://github.com/YOUR_USERNAME/daily-cli.git
cd daily-cli
chmod +x daily

# Add to PATH (zsh)
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

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

### Requirements

- macOS
- Google Chrome
- zsh (default shell on macOS)

---

## 中文

一个极简的命令行工具，一条命令打开你每日工作流需要的所有网站。

### 功能

`daily` 会在 Google Chrome 中按分类打开你每天需要的网站：

| 分类 | 网站 |
|------|------|
| **social** | X、LinkedIn、GitHub |
| **scholar** | Google Scholar、Semantic Scholar |
| **papers** | HuggingFace 每日论文 |
| **ai** | ChatGPT、Claude、Gemini |

### 安装

```bash
git clone https://github.com/YOUR_USERNAME/daily-cli.git
cd daily-cli
chmod +x daily

# 添加到 PATH（zsh）
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### 使用

```bash
daily              # 打开所有网站
daily social       # 只打开 X、LinkedIn、GitHub
daily scholar      # 只打开 Google Scholar、Semantic Scholar
daily papers       # 只打开 HuggingFace 每日论文
daily ai           # 只打开 ChatGPT、Claude、Gemini
daily social ai    # 组合多个分类
daily list         # 列出所有网址（不打开浏览器）
daily help         # 显示帮助
```

### 环境要求

- macOS
- Google Chrome
- zsh（macOS 默认 shell）

---

## License

MIT
