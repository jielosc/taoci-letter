# taoci-letter · 保研/申研套磁信生成器

一个基于开放 [Agent Skills](https://github.com/vercel-labs/skills) 协议的 skill，可在 Claude Code、Codex、Cursor、Gemini CLI 等 50+ AI agent 中使用。给出导师主页链接 + 你的背景，自动抓取导师研究方向与近期论文，按「标准七段结构 + 真诚/切题/潜力」的模式写一封个性化套磁信。

不是为了写一封"语法正确、格式漂亮"的信——那种 AI 分分钟能套出来，导师早就看腻了。目标是让导师看到邮件背后那个真实、有判断力的人。

## 安装

### 方式一：一行命令（推荐，跨 agent 通用）

```bash
npx skills add jielosc/taoci-letter
```

它会自动识别你正在用的 agent，把 skill 装到对应目录，只放 skill 本体，不会把 README 等文件塞进来。也可以用 `-a` 指定目标，如 `-a claude-code`、`-a codex`、`-a cursor`。

### 方式二：手动安装

clone 到对应 agent 的 skills 目录：

| Agent | 路径 |
|---|---|
| Claude Code | `~/.claude/skills/taoci-letter/` |
| Codex CLI | `~/.codex/skills/taoci-letter/` |
| Cursor | `~/.cursor/skills/taoci-letter/` |

```bash
git clone https://github.com/jielosc/taoci-letter.git ~/.claude/skills/taoci-letter
```

## 第一次使用：填一次背景

把示例模板复制成自己的 profile，填上真实背景：

```bash
cd ~/.claude/skills/taoci-letter   # 或你的 agent 对应目录
cp profile.example.md profile.md
# 然后用编辑器打开 profile.md，按提示填好
```

`profile.md` 已被 `.gitignore` 忽略，不会被 git 跟踪，你的 GPA/排名等信息只留在本地。

## 之后每次：只丢一个链接

**最稳的方式是显式调用**——在 Claude Code 里敲 `/taoci-letter`，或直接说"用 taoci-letter skill 帮我写"，然后带上导师链接：

> /taoci-letter 帮我给这位老师写套磁信：https://example.edu/~prof

也可以直接描述需求让它自动触发：

> 帮我给这位老师写套磁信：https://example.edu/~prof

> 提示：skill 能否自动触发由 AI 自行判断，不是 100% 保证。如果它没用上本 skill（比如直接自己写了、没按七段结构），用上面的显式调用方式最可靠。

skill 会自动读 `profile.md` 里的背景，抓导师主页，找出真实匹配点（会先列给你确认），再按七段结构出信。想临时换个突出方向，对话里直接说就行。

## 结构

```
taoci-letter/
  SKILL.md              # 触发条件 + 工作流程 + 真诚/切题/潜力三信条
  profile.example.md    # 背景模板（复制成 profile.md 填写）
  references/
    structure.md        # 标准七段：主题→称呼→背景→契合度→实力→行动→落款
```

## 写作理念

套磁信的格式（七段结构）只是底线，按它写不会犯大错。真正加分的是三点：

- **真诚**：真的看过导师研究，讲得出具体问题和自己的理解，而不是"久仰大名"。
- **切题**：翻过导师近几年论文，能猜到他接下来可能关心什么——最好正中他一直想做的题。
- **潜力**：展示对自己做过的工作的真正理解，而不是堆奖项、堆论文、堆竞赛。

## License

MIT
