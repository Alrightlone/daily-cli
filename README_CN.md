# daily-cli

> **[English](README.md)** | **中文**

四个极简工具，搭配你的每日工作流：

- **`daily`** —— 一条命令打开每天要看的网站
- **`plan`** —— 任务计划器，支持递延、周期任务、周视图、连续打卡
- **`plan-ui`** —— 同一个计划器的桌面应用窗口（大窗 + 迷你挂件）
- **`journal`** —— 每日日记，一天一个 markdown 文件

## 安装

```bash
git clone https://github.com/Alrightlone/daily-cli.git
cd daily-cli
chmod +x daily plan plan-ui journal

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
plan                             # 查看今日计划
plan add "写论文草稿"             # 添加任务
plan done 1                      # 标记任务 1 为已完成
plan half 2                      # 标记任务 2 为半完成（会提示输入原因）
plan skip 3                      # 标记任务 3 为未完成（会提示输入原因）
plan edit 1 "新的内容"            # 改写任务 1 的文字（修正笔误）
plan rm 4                        # 删除任务 4
plan clear                       # 清空今日全部任务（会二次确认）
plan week                        # 最近 7 天一览 + 连续打卡天数
plan recur add weekday "健身"     # 每个工作日自动添加"健身"
plan recur list                  # 查看所有重复任务规则
plan recur rm <id>               # 删除一条规则
plan edit                        # 用 $EDITOR 打开今日计划（JSON 源文件）
plan show 2026-04-16             # 查看历史某天的计划
plan list                        # 列出所有保存过的日期
plan help                        # 显示帮助
```

**每日自动行为**（当天第一次运行 `plan` 时）：

- **递延**：昨天的未完成任务（pending）会自动带入今天，标记 `↪`
- **周期**：当天匹配的 `recurring` 规则会自动生成任务，标记 `↻`
- **连击**：连续有任务完成的天数显示在底部

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
plan-ui              # 完整窗口
plan-ui mini         # 迷你挂件，可放在桌面角落随时提醒
plan-ui both         # 两个窗口共享同一个 server，实时双向同步
```

启动本地服务器，在 Chrome 的独立窗口里打开计划器（没有 tab、没有地址栏，
体验像原生应用）。所有改动都写到同一份 `plans/*.json`，`plan` 命令、
`plan-ui`、`plan-ui mini` 编辑的都是同一份数据。

**特性**
- 点击左侧圆圈弹出状态选择：✓ 完成 / ◐ 半完成 / ✗ 未完成（后两个会弹窗填原因）
- 鼠标悬停在任务上，显示编辑和删除按钮
- `A−` / `A+` 按钮随时调整字号（每个窗口独立记忆）
- 根据系统偏好自动切换明暗主题
- 窗口每 5 秒自动刷新，在 mini 窗或 CLI 里改的东西立即同步
- `Esc` 关闭任何弹窗或菜单

Mini 窗口是个紧凑的挂件，拖到桌面角落，随时低头一眼就能看到待办。
拖动空白区域就能移动窗口（不要拖任务或输入框）。

关掉窗口即退出，或在终端里按 `Ctrl+C`。

---

## `journal` —— 每日日记

默认弹出一个简洁的写作窗口。支持 markdown、实时预览切换、自动保存、
左右切换日期，写起来舒服。

```bash
journal                       # 打开今天的日记（UI 窗口）
journal yesterday             # 打开昨天的日记
journal 2026-04-16            # 打开指定日期

journal show 2026-04-16       # 终端：打印某天的日记
journal list                  # 终端：列出所有日记
journal help                  # 显示帮助
```

### UI 特性

- **Write / Preview 切换** —— 点击切换按钮，或按 `⌘P` / `Ctrl+P`
- **自动保存** —— 停笔 500ms 后自动存盘，不用手动保存
- **翻日记** —— 顶部 `‹` / `›` 箭头跳到前一天 / 后一天；`⌘S` / `Ctrl+S` 强制保存
- **Markdown** —— 标题、粗体、斜体、列表、引用、代码块、链接，Preview 里完整渲染
- **无干扰设计** —— 衬线字体、宽行距、极简界面，专注写作

每天一个 markdown 文件，保存在 `journal_entries/`（已 gitignore，不上传）。

## 环境要求

- macOS
- Google Chrome（`daily` 和 `plan-ui` 需要）
- Python 3（`plan` / `plan-ui` / `journal` 都需要，macOS 自带）
- zsh（macOS 默认 shell）
- 首次打开 UI 需要联网（通过 CDN 加载 Alpine.js）

## 许可证

MIT
