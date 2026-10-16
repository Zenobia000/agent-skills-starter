# agent-skills-starter

> 一個 **Claude Code 與 Codex 共用**的專案起點：38 個工程技能、agent 護欄、Git 安全閘門，開出來就能用，不用安裝。

按 GitHub 上的 **Use this template** 開一個新 repo，或 fork 下來改。

---

## 開出來之後做三件事

```bash
git config core.hooksPath .githooks     # 1. 打開 Git 安全閘門
claude                                  # 2. 或 codex
```

3. 在 agent 裡打 `/setup-skills`（Codex：`$setup-skills`）。它會問你議題放哪、領域文件放哪，寫進 `docs/agents/` —— 拆票、寫規格類的技能靠這份設定。

之後不知道用哪個技能，打 **`/compass`**（Codex：`$compass`）。

再把 `AGENTS.md` 的 ＜＞ 換成你的專案內容。

⚠️ Windows：clone **之前**先跑 `git config --global core.symlinks true`（要開「開發人員模式」），否則 Codex 找不到技能。

---

## 裡面有什麼

| 位置 | 是什麼 |
|---|---|
| `.claude/skills/` | 38 個技能：從需求拷問、規格、架構、拆票、TDD、code review 到 Git 流程。另有兩個輸出風格 `/roast`、`/seduce` |
| `.agents/skills` | 指向 `.claude/skills` 的 symlink，Codex 從這裡讀同一份 |
| `.claude/hooks/` | 兩支 agent guard：擋一次 `git add` 全部、force push、`reset --hard` 到別處、跳過 git hook、提交疑似金鑰 |
| `.claude/settings.json`／`.codex/hooks.json` | 同一對 guard，兩個工具各自登記 |
| `.githooks/` | Git 層的閘門，人和 agent 都擋 |
| `scripts/check.sh` | 一個指令檢查全部：技能 frontmatter、路由表同步、Codex 設定同步、guard 測試 |
| `AGENTS.md`／`CLAUDE.md` | 專案大腦的空白骨架 |

## 只支援 Claude Code 與 Codex

技能用「只准使用者觸發」區分編排型技能（例如 `/compass`、`/to-tickets`）。
Claude Code 讀 `SKILL.md` 的 `disable-model-invocation`，Codex 讀 `agents/openai.yaml`，兩邊由 `scripts/check-codex-skills.sh` 擋不同步。
Antigravity、Copilot 不認這個設定，編排型技能會被 agent 自己啟動。⚠️ Cursor 未驗證。

## 改技能

技能是你的，可以改。規矩只有三條，寫在 [`.claude/skills/README.md`](./.claude/skills/README.md)，改完跑：

```bash
bash scripts/check.sh
```

## 來源與授權

技能衍生自 [luca-skills](https://github.com/Luca0x5755/luca-skills)（MIT），經 [SDD-agent-coding-beginner](https://github.com/Zenobia000/SDD-agent-coding-beginner) 修改。聲明見 [`THIRD-PARTY-NOTICES.md`](./THIRD-PARTY-NOTICES.md)，**不要刪**。

想看這套技能怎麼用在一個實際題目上：[`leavebot-bootcamp`](https://github.com/Zenobia000/leavebot-bootcamp)。
