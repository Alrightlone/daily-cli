# daily-cli

> **[English](README.md)** | **中文**

三个极简工具，搭配你的每日工作流：

- **`daily`** —— 一条命令打开每天要看的网站
- **`plan`** —— 终端里管理今日计划，本地保存
- **`plan-ui`** —— 同一个计划器，以简洁的桌面应用形式打开

## 安装

```bash
git clone https://github.com/Alrightlone/daily-cli.git
cd daily-cli
chmod +x daily plan plan-ui

# 添加到 PATH（zsh）
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

---

## `daily` —— 网站一键打开

在 Google Chrome 中按分类打开你每天需要的网站：

| 分类 | 网站 |
|------|------|
| **social** | X、LinkedIn、GitHub |
| **scholar** | Google Scholar、Semantic Scholar |
| **papers** | HuggingFace 每日论文 |
| **ai** | ChatGPT、Claude、Gemini |

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

---

## `plan` —— 每日任务计划

终端里的本地任务计划表。每天的计划保存在 `plans/` 目录下（已被 `.gitignore` 排除，
**不会上传到 GitHub**，你的计划完全私密）。

任务有四种状态：

| 图标 | 状态 | 是否需要备注原因 |
|------|------|------|
| ☐ | 待办 | — |
| ✓ | 已完成 | 不需要 |
| ◐ | 半完成 | **需要** |
| ✗ | 未完成 | **需要** |

### 使用

```bash
plan                       # 查看今日计划
plan add "写论文草稿"       # 添加任务
plan done 1                # 标记任务 1 为已完成
plan half 2                # 标记任务 2 为半完成（会提示输入原因）
plan skip 3                # 标记任务 3 为未完成（会提示输入原因）
plan edit 1 "新的内容"      # 改写任务 1 的文字（修正笔误）
plan rm 4                  # 删除任务 4
plan clear                 # 清空今日全部任务（会二次确认）
plan edit                  # 用 $EDITOR 打开今日计划（JSON 源文件）
plan show 2026-04-16       # 查看历史某天的计划
plan list                  # 列出所有保存过的日期
plan help                  # 显示帮助
```

### 示例

```
  📅 2026-04-17  · Today

   1  ✓  写完论文草稿
   2  ◐  Review 三个 PR  · 只审了2个，第3个明天继续
   3  ✗  健身 1 小时  · 下雨改室内
   4  ☐  读 2 篇 HuggingFace daily paper

  ────────────────────────────────────────
  1/4 done · 1 half · 1 skipped · 1 pending
```

---

## `plan-ui` —— 桌面应用式窗口

```bash
plan-ui
```

启动本地服务器，在 Chrome 的独立窗口里打开计划器（没有 tab、没有地址栏，
体验像原生应用）。所有改动都写到同一份 `plans/*.json`，`plan` 命令和
`plan-ui` 编辑的是同一份数据。

**特性**
- 点击左侧圆圈弹出状态选择：✓ 完成 / ◐ 半完成 / ✗ 未完成（后两个会弹窗填原因）
- 鼠标悬停在任务上，显示编辑和删除按钮
- 根据系统偏好自动切换明暗主题
- `Esc` 关闭任何弹窗或菜单

关掉窗口即退出，或在终端里按 `Ctrl+C`。

---

## 环境要求

- macOS
- Google Chrome（`daily` 和 `plan-ui` 需要）
- Python 3（`plan` 和 `plan-ui` 需要，macOS 自带）
- zsh（macOS 默认 shell）
- 首次打开 UI 需要联网（通过 CDN 加载 Alpine.js）

## 许可证

MIT
