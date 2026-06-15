# Usage Workflow

# 使用工作流

本文件说明如何使用 `macro-chain-research-skill` 完成宏观产业链研究、单家公司分析和候选研究池更新。

本文件是使用指南，不是自动化工具。  
本项目不内置数据接口、不自动联网、不自动调用金融数据库，也不执行任何交易操作。

所有输出仅用于研究辅助，不构成投资建议。

---

## 1. 使用逻辑

1. 先选择研究任务；
2. 再选择对应 Prompt；
3. 提供主题、公司或候选池信息；
4. 提供可用数据或材料；
5. 让 AI 按 Prompt 输出结构化结果；
6. 将结果记录到候选研究池模板；
7. 后续基于新增证据进行更新。

---

## 2. 文件分工

| 文件 | 作用 |
|---|---|
| `skill.yaml` | 定义 Skill 的身份、范围、输入输出和边界 |
| `prompts/system.md` | 定义通用规则和禁止事项 |
| `prompts/weekly_research.md` | 执行周度主题研究 |
| `prompts/stock_analysis.md` | 执行单家公司分析 |
| `prompts/candidate_pool_update.md` | 执行候选研究池更新 |
| `schemas/research_input.schema.json` | 定义研究输入结构 |
| `schemas/company_analysis.schema.json` | 定义公司分析输出结构 |
| `schemas/candidate_pool.schema.json` | 定义候选池输出结构 |
| `templates/candidate_pool_template.md` | 记录候选研究池 |
| `examples/demo_robot_industry.md` | 展示使用示例 |
| `DISCLAIMER.md` | 项目免责声明 |

---

## 3. 选择任务类型

### 任务一：研究一个宏观主题或产业主题

适用场景：

- 想研究某个产业方向；
- 想拆解产业链；
- 想找可能的供需瓶颈；
- 想形成初步候选研究池。

使用文件：

- `prompts/system.md`
- `prompts/weekly_research.md`
- `templates/candidate_pool_template.md`

### 任务二：分析单家公司

适用场景：

- 想判断某家公司是否真实参与某个产业链；
- 想核验公司是否只是概念相关；
- 想判断业务纯度、证据等级和风险；
- 想决定是否放入候选研究池。

使用文件：

- `prompts/system.md`
- `prompts/stock_analysis.md`
- `schemas/company_analysis.schema.json`
- `templates/candidate_pool_template.md`

### 任务三：更新候选研究池

适用场景：

- 已经有候选池；
- 新增了公告、财报、行业数据或风险事件；
- 需要判断候选项是否升级、降级、保留或排除。

使用文件：

- `prompts/system.md`
- `prompts/candidate_pool_update.md`
- `schemas/candidate_pool.schema.json`
- `templates/candidate_pool_template.md`

---

## 4. 数据模式

### Mode 1：无可靠数据

只有主题或公司名，缺少公告、财报、研报、新闻或数据库结果。

允许输出：

- 研究框架；
- 产业链初步拆解；
- 数据需求清单；
- 待验证问题。

不应输出：

- 第一梯队公司；
- 强确定性结论；
- 明确排序；
- 类似投资建议的表达。

### Mode 2：用户提供数据

用户提供公告、财报、新闻、研报、数据库结果、表格或其他材料。

允许输出：

- 基于材料的结构化分析；
- 证据等级；
- 风险判断；
- 候选池初步分层；
- 后续验证任务。

### Mode 3：可访问数据

模型环境可以联网或调用数据库，用户提供了可查询的数据源。

允许输出更完整的主题研究、公司映射、候选池分层、风险判断和后续验证任务。

仍然禁止输出买入、卖出、持有、目标价、仓位建议或短线交易信号。

---

## 5. 推荐使用步骤

1. 复制 `prompts/system.md`；
2. 选择对应任务 Prompt；
3. 提供输入信息和数据材料；
4. 要求 AI 先判断数据模式；
5. 输出结果；
6. 记录到 `templates/candidate_pool_template.md`；
7. 后续根据新增证据更新候选池。

---

## 6. 候选池更新规则

候选池更新必须基于新增证据或新增风险。

可以触发更新的情况：

- 新公告；
- 新财报；
- 新订单；
- 新产能；
- 新客户；
- 新认证；
- 新政策；
- 新招投标；
- 新行业数据；
- 新上下游验证信息；
- 新财务、治理或监管风险。

不应触发更新的情况：

- 只有股价上涨；
- 只有股价下跌；
- 只有市场讨论增加；
- 只有社交媒体传闻；
- 只有用户主观看好；
- 没有新增证据。

---

## 7. 最低合格输出标准

一次合格的研究输出，至少应该包含：

- 数据模式判断；
- 主题或公司背景；
- 产业链位置；
- 证据等级；
- 风险判断；
- 候选池分层或不分层原因；
- 后续验证任务；
- 免责声明。

如果资料不足，应明确写出：

当前缺少可靠数据，本次仅输出研究框架和待验证问题，不形成高优先级候选研究池。

---

## 8. 最终提醒

本项目是轻量化 AI Skill Package，不是 AI Agent。  
本项目不内置 tool，不内置数据源，不自动联网。  
所有数据需要用户自行提供或在支持数据访问的模型环境中查询。  
所有输出仅用于研究辅助，不构成投资建议。
