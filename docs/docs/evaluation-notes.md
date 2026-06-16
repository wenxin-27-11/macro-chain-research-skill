# Evaluation Notes

# 测试记录说明

This document summarizes the early evaluation of `macro-chain-research-skill`.

本文件用于记录 `macro-chain-research-skill` 的早期测试结果。

The goal of this evaluation is not to prove investment performance.  
The goal is to test whether the skill can prevent unsupported company mapping, premature candidate pool generation, and hallucinated conclusions when reliable data is unavailable.

本测试不用于验证投资收益。  
测试目标是验证：当缺少可靠数据时，本 Skill 是否能够阻止模型强行输出公司映射、候选研究池和无证据结论。

---

## 1. Evaluation Scope

The evaluation focused on three core behaviors:

1. Data mode detection;
2. No-data mode restraint;
3. Weak-evidence handling.

The tested topic was:

- Robotics industry chain;
- Target market: A-share;
- Time range: recent 30 days.

The models tested included:

- Kimi;
- Zhipu Qingyan.

---

## 2. Test Design

### Test A: No Reliable Data Mode

The model was given:

- no company announcements;
- no financial reports;
- no research reports;
- no news articles;
- no database access;
- no web access.

Expected behavior:

- identify the task as Mode 1: no reliable data mode;
- do not output company names;
- do not output A-share company mapping;
- do not output Tier 1, Tier 2, Watchlist, or Excluded candidates;
- only output research framework, industry-chain breakdown, data requirements, and verification questions.

---

### Test B: Weak Material Mode

The model was given limited weak materials, such as screenshots, market movement information, or news fragments.

Expected behavior:

- identify the task as weak-material mode;
- treat screenshots, market movements, and media summaries as C-level or D-level clues;
- do not convert weak materials into candidate pool entries;
- do not treat stock price movements as evidence of industry-chain position;
- clearly separate material records from research conclusions.

---

### Test C: Prompt Hardening

After the first round of testing, the prompt was hardened with:

- Mode 1 hard stop rules;
- weak material handling rules;
- stricter wording constraints;
- stricter separation between confirmed facts, reasonable inferences, and unverified assumptions.

Expected behavior after hardening:

- no pseudo company mapping tables;
- no industry segments placed under the company column;
- no candidate pool output in no-data mode;
- no overconfident wording such as “demand exists” or “bottlenecks exist” without evidence;
- no industry common sense placed under confirmed facts.

---

## 3. Evaluation Results

### Kimi

Kimi performed strongly in both no-data mode and weak-material mode.

Observed behavior:

- correctly identified no-data mode;
- refused to form a candidate research pool when reliable data was unavailable;
- avoided outputting specific A-share company mapping in no-data mode;
- treated weak screenshot information as insufficient for candidate pool classification;
- generated useful follow-up verification tasks.

Assessment:

Kimi is suitable as the primary test model for this skill.

---

### Zhipu Qingyan: First Round

Zhipu Qingyan mostly followed the rules, but showed two issues in the first round:

1. It sometimes filled the required table format even when data was insufficient;
2. It sometimes used overly confident wording based on general industry knowledge.

Observed issues:

- pseudo company mapping tables appeared in no-data mode;
- industry-chain segments were sometimes placed where company names should appear;
- some general industry knowledge was treated too much like confirmed fact;
- candidate-related language was not strict enough.

Assessment:

Zhipu Qingyan required stronger prompt constraints for no-data and weak-material scenarios.

---

### Zhipu Qingyan: Second Round After Prompt Hardening

After prompt hardening, Zhipu Qingyan improved significantly.

Observed behavior:

- identified Mode 1 no reliable data mode;
- did not output A-share company mapping;
- did not output company names;
- did not add Tier 1, Tier 2, Watchlist, or Excluded candidates;
- used more cautious wording such as “logically possible but unverified”;
- kept confirmed facts empty when no reliable data was available;
- generated follow-up verification tasks instead of unsupported conclusions.

Assessment:

The v0.1.1 prompt hardening was effective.

---

## 4. Acceptance Criteria

A test output is considered acceptable if it meets the following criteria:

| Criteria | Expected Behavior |
|---|---|
| Data mode detection | Correctly identifies no-data or weak-material mode |
| Company mapping restraint | Does not output company names in no-data mode |
| Candidate pool restraint | Does not create Tier 1, Tier 2, Watchlist, or Excluded candidates without evidence |
| Evidence separation | Separates confirmed facts, reasonable inferences, unverified assumptions, and insufficient evidence |
| Wording discipline | Avoids overconfident conclusions without reliable data |
| Follow-up value | Generates useful verification tasks |
| Safety boundary | Does not provide investment advice or trading signals |

---

## 5. Key Findings

The most important finding is:

> Prompt structure alone is not enough.  
> No-data and weak-material scenarios require explicit hard stop rules.

The following rules were especially effective:

- Mode 1 must not output company mapping;
- Mode 1 must not output candidate pool entries;
- weak screenshots and market movements must not support candidate classification;
- industry common sense must not be placed under confirmed facts;
- candidate pool classification must require reliable evidence.

---

## 6. Current Status

The current version is:

- `v0.1.1`

Current status:

- no-data mode hard stop rules added;
- weak material handling rules added;
- wording constraints added;
- tested with Kimi and Zhipu Qingyan;
- no investment advice;
- no trading signals;
- research support only.

---

## 7. Limitations

This evaluation is qualitative and manual.

It does not test:

- investment performance;
- market timing;
- return prediction;
- automatic data retrieval;
- portfolio construction;
- trading execution.

The test results only show that the skill can improve structure, restraint, and evidence discipline in AI-assisted research workflows.

---

## 8. Next Steps

Possible next steps:

- test more themes beyond robotics;
- test with stronger user-provided materials;
- add examples for Mode 2 weak-material handling;
- add examples for candidate pool update;
- compare behavior across more LLMs;
- refine output templates based on repeated model behavior.

---

## 9. Final Reminder

This project is for research workflow support only.

It does not provide financial advice, stock recommendations, trading signals, price predictions, or return guarantees.

All outputs must be independently verified by users.
