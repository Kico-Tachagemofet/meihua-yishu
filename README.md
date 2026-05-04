# 梅花易数 AI Skill

一套完整的梅花易数（含梅花新易）断卦流程，设计用于 AI agent 的 skill 系统。

## 文件结构

```
meihua-yishu/
├── SKILL.md                              # 主 skill：七步硬流程
├── references/
│   ├── meihua-yishu.md                   # 八卦取象表、五行旺衰、六十四卦速查、应期断法
│   └── meihua-xinyi-method.md            # 《梅花新易》方法论：万物起卦、一卦多断、外应比拟
├── scripts/
│   └── yijing_draw.py                    # 易经起卦脚本（Python 标准库，零依赖）
└── README.md
```

## 使用方式

### 作为 AI Agent Skill

将此目录放入你的 AI agent 的 skills 路径中。触发条件：用户提出梅花易数/易经断卦请求。

可用于：
- **Claude Code** agent
- **Hermes** skill 系统
- 其他兼容 tool-calling 的 AI 工具

### 起卦脚本

```bash
python3 scripts/yijing_draw.py
```

输出：随机数、本卦、之卦、变爻位置。仅使用 Python 标准库，无外部依赖。也可用「万物起卦入口表」中的手动方法（时分、报数、字画、外应等）。

### 配套工具

`yijing_draw.py` 可配合 [SpiritTool](https://github.com/Kico-Tachagemofet/Project-Hermes) 桌面应用使用。

## 断卦流程

1. **问题结构分析** — 明确问题域、求测主体、颗粒度
2. **起卦** — 脚本或手动入口
3. **排主互变 + 定体用** — 动爻定位体用
4. **八卦象意速查** — 14 范畴完整列出
5. **取象表** — AI 选择 + 画面互动
6. **体用生克 + 旺衰 + 主互变三段**
7. **直读 / 外应 / 比拟 + 自检 + 整合**

每次断卦走完整七步。输出前强制三步自检（五行归属、体用判定、卦德验证）。

## License

MIT
