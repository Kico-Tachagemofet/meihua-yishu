# 梅花易数 AI Skill

梅花易数 / 梅花新易断卦流程 Skill，设计给 Hermes、Claude Code、Codex、龙虾等 AI Agent 使用。它把起卦、体用、生克、旺衰、主互变、取象、外应、自检整理成可执行流程。

这一版承担的工作是：让 AI 稳定走完梅花流程，减少随口解释卦象、跳过体用或取象表的情况。

## 适合谁

- 想让 AI Agent 按梅花易数流程断卦。
- 已经用 `spirit-communication-system v5.1 Lite` 抽到了易经本卦、变爻、之卦，想继续做梅花分析。
- 想把八卦取象、体用生克、主互变三段、外应和自检固定下来。
- 想训练 AI 先列取象，再出结论。

## 推荐搭配

日常推荐工作流：

1. 用 [spirit-communication-system v5.1 Lite](https://github.com/Kico-Tachagemofet/spirit-communication-system-lite) 抽取原始符号材料。
2. 如果结果里有易经本卦、变爻、之卦，调用本 Skill。
3. 如果同一轮里还有塔罗，用 [Symbol Anchor Check](https://github.com/Kico-Tachagemofet/symbol-anchor-check) 检查塔罗属性。
4. 使用者结合问题语境和现实边界判断是否继续追问。

## 文件结构

```text
meihua-yishu/
├── README.md
├── SKILL.md
└── references/
    ├── meihua-yishu.md          # 八卦取象、五行旺衰、六十四卦速查、应期断法
    └── meihua-xinyi-method.md   # 起卦入口、主互变、一卦多断、外应、比拟、训练法
```

当前公开包包含 Skill 和 references。起卦脚本可以使用本仓库自带的 `scripts/yijing_draw.py`（若已放入），也可以使用 v5.1 Lite 的 `scripts/yijing_draw.py`，或接入自己的 I Ching 起卦脚本。

## 核心流程

每次断卦走七步：

1. **问题结构分析**：问题域、求测主体、颗粒度、第一念。
2. **起卦**：脚本起卦或手动入口，例如时分、报数、字画、外应。
3. **排主互变 + 定体用**：确定本卦、互卦、之卦、动爻、体卦、用卦。
4. **八卦象意速查**：列出涉及经卦的 14 类象意。
5. **取象表**：从原始物象、问题域、形性声色味等角度选择取象。
6. **体用生克 + 旺衰 + 主互变三段**：判断当前状态、内因和转化方向。
7. **直读 / 外应 / 比拟 + 自检 + 整合**：输出前检查五行、体用、卦德和取象来源。

## Prompt 版与 Skill 版

轻量 prompt 可以提醒 AI 按体用、生克、主互变分析。完整版更适合作为 Skill：

- 需要 references 中的取象表和方法论。
- 需要每次固定走七步，防止跳步。
- 需要在结论前列取象表。
- 需要检查五行归属、体用判定和卦德是否被违反。
- 需要配合起卦脚本或 v5.1 Lite 输出的卦象数据。

当一个任务需要固定流程、查表和输出前自检，Agent Skill 会比单段 prompt 稳定。

## 使用方式

### 作为 AI Agent Skill

把本目录放入 Agent 的 skills 路径中。触发条件：

- 用户提出梅花易数、易经断卦、卦象分析请求。
- 用户提供本卦、变爻、之卦。
- 用户使用 v5.1 Lite 抽取易经结果后要求继续解读。

适用环境：

- Hermes
- Claude Code
- Codex
- 龙虾
- 其他支持 Skill、tool-calling 或本地脚本调用的 AI Agent

### 配合起卦脚本

如果使用 v5.1 Lite：

```bash
python3 scripts/yijing_draw.py
```

输出本卦、变爻、之卦后，把结果交给本 Skill 继续分析。

如果使用其他起卦方式，请提供：

- 本卦
- 变爻位置
- 之卦
- 起卦时间或起卦入口
- 问题语境

## 来源与边界

本项目包含四类内容：

1. 传统来源：《梅花易数》中的体用、生克、主互变、取象和应期思路。
2. 方法扩展：《梅花新易》中的万物起卦、一卦多断、外应、比拟和训练法。
3. 作者整理：七步硬流程、取象表输出结构、AI Agent 自检规则。
4. 程序生成：起卦脚本输出的本卦、变爻、之卦；脚本可以来自本仓库、v5.1 Lite 或使用者自己的起卦工具。

本项目用于梅花易数学习、符号分析、个人记录、创作和实验性 Agent 工作流。它不提供现实决策担保，不替代医疗、法律、财务或心理咨询建议。

## License

MIT
