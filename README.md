# taoci-letter · 保研/申研套磁信生成器

一个 [Claude Code](https://claude.com/claude-code) skill。给出导师主页链接 + 你的背景，自动抓取导师研究方向与近期论文，按「标准七段结构 + 真诚/切题/潜力」的模式写一封个性化套磁信。

不是为了写一封"语法正确、格式漂亮"的信——那种 AI 分分钟能套出来，导师早就看腻了。目标是让导师看到邮件背后那个真实、有判断力的人。

## 安装

把这个 skill 放到 Claude 的 skills 目录下即可（个人全局生效）：

```bash
git clone https://github.com/<your-name>/taoci-letter.git ~/.claude/skills/taoci-letter
```

或者下载 zip，解压后整个文件夹放进 `~/.claude/skills/`。

## 第一次使用：填一次背景

把示例模板复制成自己的 profile，填上真实背景：

```bash
cd ~/.claude/skills/taoci-letter
cp profile.example.md profile.md
# 然后用编辑器打开 profile.md，按提示填好
```

`profile.md` 已被 `.gitignore` 忽略，不会被 git 跟踪，你的 GPA/排名等信息只留在本地。

## 之后每次：只丢一个链接

在 Claude Code 里直接说：

> 帮我给这位老师写套磁信：https://example.edu/~prof

skill 会自动读 `profile.md` 里的背景，抓导师主页，找出真实匹配点（会先列给你确认），再按七段结构出信。想临时换个突出方向，对话里直接说就行。

## 结构

```
taoci-letter/
  SKILL.md              # 触发条件 + 工作流程 + 真诚/切题/潜力三信条
  profile.example.md    # 背景模板（复制成 profile.md 填写）
  references/
    structure.md        # 标准七段：主题→称呼→背景→契合度→实力→行动→落款
    checklist.md        # 生成后自检：格式 + top 平台加分项
```

## 写作理念

套磁信的格式（七段结构）只是底线，按它写不会犯大错。真正加分的是三点：

- **真诚**：真的看过导师研究，讲得出具体问题和自己的理解，而不是"久仰大名"。
- **切题**：翻过导师近几年论文，能猜到他接下来可能关心什么——最好正中他一直想做的题。
- **潜力**：展示对自己做过的工作的真正理解，而不是堆奖项、堆论文、堆竞赛。

## License

MIT
