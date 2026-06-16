# Macro Chain Research Skill

# 宏观产业链研究 Skill

A lightweight AI Skill Package for macro-chain research, evidence verification, anti-hallucination checks, and A-share candidate research pool management.

一个轻量化的 AI 宏观产业链研究 Skill Package，用于宏观主题研究、产业链拆解、供需瓶颈识别、证据核验、反幻觉检查和 A 股候选研究池管理。

This project is designed for research workflow support only. It does not provide financial advice, stock recommendations, trading signals, price predictions, or return guarantees.

本项目仅用于研究辅助，不构成投资建议、证券推荐、交易信号、价格预测或收益承诺。

---

## Why This Project Is Different

Many AI investment research prompts stop at generating a list of related companies.

This project is designed to be more structured, more conservative, and easier to reuse.

It is not a one-shot prompt. It is a lightweight Skill Package with:

* a skill definition file;
* reusable task prompts;
* structured input and output schemas;
* evidence-level rules;
* anti-hallucination checks;
* candidate research pool templates;
* usage workflow documentation;
* fictional examples for safe demonstration.

The key difference is that this project does not ask AI to directly “find stocks”.

Instead, it asks AI to:

1. identify the macro theme;
2. map the industry chain;
3. locate possible supply-demand bottlenecks;
4. verify company exposure with evidence;
5. separate facts, inferences, assumptions, and insufficient evidence;
6. classify companies into a research pool;
7. generate follow-up verification tasks.

If reliable data is not available, the model must not output high-priority candidates or strong conclusions.

This makes the project closer to a structured research workflow than a simple stock-picking prompt.

---

## 这个项目和普通 Prompt 有什么不同？

很多投研类 Prompt 只会让 AI 输出一批相关公司名单。

本项目更关注结构化、证据约束、反幻觉和长期候选池管理。

它不是一次性 Prompt，而是一个轻量化 Skill Package，包含：

* Skill 定义文件；
* 可复用任务 Prompt；
* 输入输出 Schema；
* 证据等级规则；
* 反幻觉检查；
* 候选研究池模板；
* 使用工作流说明；
* 安全的虚构示例。

本项目不要求 AI 直接“找股票”。

它要求 AI 先完成：

1. 识别宏观主题；
2. 拆解产业链；
3. 判断可能的供需瓶颈；
4. 用证据核验公司真实业务关联；
5. 区分事实、推断、假设和证据不足；
6. 将公司放入候选研究池；
7. 生成后续验证任务。

如果缺少可靠数据，模型不得输出第一梯队候选或强结论。

因此，它更接近一套结构化研究工作流，而不是简单的选股 Prompt。

---

## 30-Second Quick Start
1. Copy prompts/system.md
2. Copy one task prompt:
   - weekly_research.md
   - stock_analysis.md
   - candidate_pool_update.md
3. Paste them into your LLM tool.
4. Provide your theme, company, or candidate pool.
5. Bring your own data.
6. Review the evidence level and follow-up verification tasks.

## 30 秒快速开始

1. 复制 prompts/system.md
2. 选择一个任务 Prompt
3. 粘贴到你的大模型工具中
4. 输入研究主题、公司或候选池
5. 自行提供数据
6. 查看证据等级、风险和后续验证任务


## 1. 项目定位

`macro-chain-research-skill` 不是自动选股 Agent，也不是自动交易系统。

它是一个轻量化 AI Skill Package，包含：

- Skill 元信息；
- 系统 Prompt；
- 周度研究 Prompt；
- 单家公司分析 Prompt；
- 候选研究池更新 Prompt；
- 输入输出 Schema；
- 候选研究池模板；
- 使用工作流说明；
- 示例文件；
- 免责声明。

它的目标是帮助使用者把一个宏观主题或产业热点拆解为：

- 真实需求来源；
- 产业链结构；
- 可能的瓶颈环节；
- 相关 A 股公司；
- 证据等级；
- 风险点；
- 候选研究池；
- 后续验证任务。

---

## 2. 本项目不是什么

本项目不是：

- 荐股工具；
- 投资顾问；
- 自动选股 Agent；
- 自动交易系统；
- 行情预测模型；
- 目标价生成器；
- 仓位管理工具；
- 内幕信息分析工具。

本项目不会也不应该输出：

- 买入建议；
- 卖出建议；
- 持有建议；
- 目标价；
- 仓位建议；
- 短线交易信号；
- 确定性收益判断。

---

## 3. 方法论来源

本项目参考中文投资社区中公开传播的 Serenity 式产业链研究思路，并将其整理为更结构化、可复用、可审计的 AI Skill Package。

本项目关注的不是“哪个股票最热”，而是：

- 真实需求来自哪里；
- 产业链中哪个环节更接近瓶颈；
- 哪些公司真实参与相关业务；
- 哪些证据可以支持判断；
- 哪些结论仍然只是推断或假设；
- 哪些公司应该进入候选研究池；
- 哪些公司应该暂时排除或继续观察。

本项目与任何个人、机构或社区没有官方关联。

---

## 4. 核心原则

1. 先看宏观主题，再拆产业链；
2. 先找真实需求，再看市场热度；
3. 先识别瓶颈环节，再映射公司；
4. 先核验证据，再形成研究优先级；
5. 先识别风险，再进入候选池；
6. 没有可靠数据时，不输出强结论；
7. 候选池分层只代表研究优先级，不代表投资建议。

---

## 5. 数据模式

本项目不内置金融数据接口，也不内置行情、财报、公告或数据库工具。

使用者需要自行提供数据，或在支持联网、数据库查询、公告检索的大模型环境中使用。

### Mode 1：无可靠数据模式

适用于用户只提供主题，且没有可靠数据源的情况。

此时只能输出：

- 研究框架；
- 产业链初步拆解；
- 数据需求清单；
- 待验证问题。

不得输出：

- 第一梯队公司；
- 强确定性结论；
- 明确公司排序；
- 类似投资建议的表达。

### Mode 2：用户提供数据模式

适用于用户提供公告、财报、研报、新闻、数据库结果或其他材料的情况。

此时可以基于用户提供的材料输出：

- 产业链拆解；
- 公司映射；
- 证据等级；
- 风险判断；
- 候选研究池初步分层；
- 后续验证任务。

但必须说明结论仅基于用户提供材料。

### Mode 3：可访问数据模式

适用于用户使用的模型环境可以联网、调用数据库或查询公开资料的情况。

此时可以输出更完整的研究结果，但仍然不能输出投资建议、交易建议或收益承诺。

---

## 6. 项目结构

```text
macro-chain-research-skill/
├── README.md
├── DISCLAIMER.md
├── LICENSE
├── skill.yaml
├── prompts/
│   ├── system.md
│   ├── weekly_research.md
│   ├── stock_analysis.md
│   └── candidate_pool_update.md
├── schemas/
│   ├── research_input.schema.json
│   ├── company_analysis.schema.json
│   └── candidate_pool.schema.json
├── templates/
│   └── candidate_pool_template.md
├── docs/
│   └── usage_workflow.md
└── examples/
    └── demo_robot_industry.md
```

---

## 7. 快速开始

### Step 1：选择任务类型

如果你想研究一个主题，使用：

`prompts/weekly_research.md`

如果你想分析一家公司，使用：

`prompts/stock_analysis.md`

如果你想更新已有候选池，使用：

`prompts/candidate_pool_update.md`

### Step 2：准备数据

可使用以下材料：

- 公司公告；
- 年报、半年报、季报；
- 招股书；
- 交易所问询函；
- 监管文件；
- 行业报告；
- 机构研报；
- 政府文件；
- 招投标数据；
- 财经媒体；
- 用户自行整理的数据表格。

如果没有可靠数据，请不要要求模型输出强结论。

### Step 3：复制 Prompt 给大模型

将以下内容组合使用：

1. `prompts/system.md`
2. 对应任务 Prompt
3. 你的研究主题或公司
4. 你提供的数据或资料

### Step 4：记录到候选研究池

将输出结果整理到：

`templates/candidate_pool_template.md`

候选池分层包括：

- 第一梯队；
- 第二梯队；
- 观察池；
- 排除池。

注意：候选池分层只代表研究优先级，不代表投资建议。

---

## 8. 证据等级

### A 级证据

公司公告、年报、半年报、季报、招股书、交易所问询函、监管文件、官方披露的产能、订单、客户或认证信息。

### B 级证据

行业协会数据、政府文件、招投标数据、产业数据库、机构研报、上下游公告交叉验证。

### C 级证据

财经媒体、行业新闻、专家访谈、会议纪要、非官方调研摘要。

### D 级证据

社交媒体观点、论坛讨论、无来源截图、未经证实的市场传闻。

规则：

- A 级和较强 B 级证据可以支持较强研究结论；
- C 级只能作为研究线索；
- D 级只能作为待验证假设；
- 只有 C 级或 D 级证据时，不得进入第一梯队；
- 证据不足时，必须明确写出证据不足。

---

## 9. 候选研究池分层

### 第一梯队

产业链位置清晰，接近关键瓶颈，证据等级较高，业务关联度较强，风险可识别但尚未直接否定逻辑。

### 第二梯队

主题相关性较强，有部分证据支持，但业务占比、客户、订单、产能或盈利贡献仍需进一步核验。

### 观察池

与主题相关，但证据较弱、业务位置模糊，或市场讨论多于公司披露。

### 排除池

证据不足、概念炒作、相关业务占比过低、基本面恶化、估值明显透支，或财务、治理、监管风险较高。

---

## 10. 适合谁使用

适合：

- 希望用 AI 辅助产业链研究的人；
- 希望把热点主题拆解为研究任务的人；
- 希望建立候选研究池的人；
- 希望降低 AI 幻觉和概念误判的人；
- 使用 ChatGPT、Kimi、Claude、通义、DeepSeek 等模型进行研究辅助的人。

不适合：

- 想直接获得股票买卖建议的人；
- 想获得短线交易信号的人；
- 想让 AI 自动选股或自动交易的人；
- 不愿意核验公告、财报和证据的人；
- 把 AI 输出当作确定性结论的人。

---

## 11. Roadmap

### v0.1

- Skill 元信息；
- 系统 Prompt；
- 周度研究 Prompt；
- 单家公司分析 Prompt；
- 候选研究池更新 Prompt；
- 输入输出 Schema；
- 候选研究池模板；
- 使用工作流说明；
- 示例；
- 免责声明。

### v0.2

- 增加更多行业示例；
- 增加飞书多维表格字段模板；
- 增加月度复盘模板；
- 增加研究报告示例。

### v0.3

- 增加更多模型适配说明；
- 增加输出质量评估样例；
- 增加更多脱敏研究案例。

注意：v0.1 不做 AI Agent，不做自动化数据接口，不做自动交易。

---

## 12. License

MIT License

---

## 13. Final Reminder

Research support only.  
Not financial advice.  
Bring your own data.  
Verify everything independently.

仅用于研究辅助。  
不构成投资建议。  
请自行提供并核验数据。  
所有结论都需要人工复核。
