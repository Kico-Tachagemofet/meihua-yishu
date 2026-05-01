# 梅花易数解读系统

> 八卦取象、体用生克、卦象推演 — Claude Code Agent / Hermes Skill

## 这是什么

这是给 **AI Agent 使用的系统配置**（skill / agent prompt），不是独立应用程序。

可以直接作为：
- **Claude Code** 的 agent 配置（放入 `.claude/agents/` 目录）
- **Hermes** 的 skill（放入 `~/.hermes/skills/` 目录）
- 其他兼容 OpenAI tool-calling 的 AI 工具的 system prompt

加载后，AI 会按照梅花易数方法论进行完整的卦象解读：定体用 → 五行生克 → 取象推演 → 之卦趋势 → 爻辞指引 → 季节旺衰校准。

## 配套工具

本系统的 `yijing_draw.py` 可以配合 [SpiritTool](https://github.com/Kico-Tachagemofet/Project-Hermes) 桌面应用使用，也可以直接命令行调用。

## 使用方式

### 作为 Claude Code Agent

将 `meihua-yishu.md` 放入项目的 `.claude/agents/` 目录：

```yaml
# .claude/agents/meihua-yishu.md
---
name: meihua-yishu
description: "梅花易数解读 — 八卦取象、体用生克、卦象推演"
model: opus
---
# ... 文档其余内容
```

### 作为 Hermes Skill

```bash
cp meihua-yishu.md ~/.hermes/skills/divination/
```

调用方式：在聊天中提及易经占卜需求，Hermes 会自动加载此 skill。

### 脚本使用

```bash
# 易经起卦
python3 scripts/yijing_draw.py
```

输出：本卦、变爻、之卦。仅使用 Python 标准库，无外部依赖。

## 项目结构

```
meihua-yishu/
├── meihua-yishu.md     # Agent / Skill 系统文档
├── scripts/
│   └── yijing_draw.py  # 易经起卦脚本
└── README.md
```

## 解读框架

1. **定体用** — 变爻在下卦则下为用上为体
2. **五行生克** — 用生体大吉，体用比和吉，用克体凶
3. **取象推演** — 上下卦物象在同一画面中互动
4. **之卦趋势** — 新的体用关系揭示未来格局
5. **爻辞指引** — 变爻爻辞是最直接的信息
6. **季节旺衰** — 校准力量对比

文档包含：八卦取象表（乾兑离震巽坎艮坤）、六十四卦速查、五行生克、季节旺衰、应期断法、驿马桃花。

## 依赖

Python 3.10+，仅使用标准库。

## License

MIT
