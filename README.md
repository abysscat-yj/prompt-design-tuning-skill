# Prompt Design & Tuning Skill

### Turn prompt tuning from guesswork into engineering.

---

## Without This Skill vs. With This Skill

<table>
<tr>
<th width="50%"> Without Skill — Agent "Freestyle" </th>
<th width="50%"> With Skill — Structured Workflow </th>
</tr>
<tr>
<td>

You say "help me optimize this prompt"

Agent rewrites the whole prompt on vibes

You eyeball a few outputs: "looks okay I guess"

Agent tweaks again... and again... and again...

You lose track of what changed and why

Something breaks in production — no one knows which edit caused it

**Result: hours burned, no confidence, no reproducibility**

</td>
<td>

You say "help me optimize this prompt"

Agent freezes a task spec first, asks you to confirm (Gate A)

Agent writes target prompt + separate judge prompt (Gates B & C)

Agent runs batch evaluation with metrics, logs every change

Each iteration has a hypothesis, a diff, and a score delta

Final candidate comes with a full report — you approve or reject (Gate E)

**Result: versioned, measurable, auditable, ready for production**

</td>
</tr>
</table>

---

## What Makes This Skill Different

| Dimension | Bare Agent | + This Skill |
|-----------|-----------|--------------|
| **Process** | Chat-style back-and-forth | 8-phase pipeline with 5 human gates |
| **Evaluation** | "Looks good to me" | Independent judge prompt + structured scoring |
| **Iteration** | Random tweaks | Hypothesis-driven, with diff and predicted impact |
| **Tracking** | Scroll up in chat history | Experiment log with version, metrics, cost per round |
| **Cost** | Unknown spend, no budget | TPM/RPM-aware, max 2 high-cost rounds by default |
| **Failure analysis** | "It sometimes gets it wrong" | 11-category failure taxonomy with cluster detection |
| **Deliverables** | A prompt in a chat message | 9 production artifacts: specs, prompts, scripts, reports |
| **Confidence** | "The agent said it's good" | Metrics-backed recommendation with known failure modes |

---

## The Workflow

```
Phase 0        Phase 1          Phase 2          Phase 3
Task Spec  -->  Target Prompt -->  Judge Prompt -->  Eval Plan
   |               |                  |                |
 Gate A          Gate B             Gate C             |
 confirm         confirm            confirm            |
 task def        direction          fairness           v
                                                 Phase 4-6
                                              Generate + Evaluate
                                                       |
                                                     Gate D
                                                  approve budget
                                                       |
                                                    Phase 7
                                                 Analyze + Iterate
                                                       |
                                                    Phase 8
                                              Final Recommendation
                                                       |
                                                     Gate E
                                                  launch review
```

**You approve at the gates. The agent handles everything in between.**

---

## Key Features

- **Separation of Concerns** — Target prompt and judge prompt are developed and versioned independently. No mixing gains.
- **Hypothesis-Driven** — Every round states what it expects to improve and what might regress. No "let's just try."
- **Full Experiment Log** — Version, changes, hypothesis, metrics, cost, and conclusion — every round, automatically.
- **Budget Guard** — Max 2 high-cost rounds by default. Early stopping when gains plateau. Human approval before spending.
- **Failure Taxonomy** — 11 categories: task misunderstanding, reasoning errors, hallucinations, format issues, constraint violations, and more.
- **Two Modes** — *Design-only* (no API needed, outputs drafts and plans) or *Execution* (end-to-end with real model calls).

---

## Deliverables

| Category | Files |
|----------|-------|
| Specification | `docs/task_spec.md`, `docs/eval_plan.md` |
| Prompts | `prompts/production_prompt_v{n}.md`, `prompts/judge_prompt_v{n}.md` |
| Scripts | `scripts/run_generation.py`, `scripts/run_judge.py` |
| Reports | `reports/iteration_{n}_summary.md`, `reports/final_recommendation.md`, `reports/experiment_log.md` |

---

## Quick Start

### Install

```bash
claude skill install abysscat-yj/prompt-design-tuning-skill
```

### Trigger

Say any of these to Claude Code:

- *"Help me design and tune this prompt"*
- *"Write the target prompt, then the judge, then run evaluation"*
- *"Find the best prompt across these models within my budget"*
- *"Run 1-2 prompt iteration rounds with cost control"*
- *"Automate this prompt tuning workflow"*

---

## License

MIT

---

<br>

# Prompt 设计调优 Skill

### 把 prompt 调优从玄学变成工程。

---

## 没有这个 Skill vs. 有这个 Skill

<table>
<tr>
<th width="50%"> 没有 Skill — Agent "自由发挥" </th>
<th width="50%"> 有 Skill — 结构化工程流程 </th>
</tr>
<tr>
<td>

你说："帮我优化一下这个 prompt"

Agent 凭感觉把整个 prompt 重写一遍

你肉眼看几条输出："好像还行吧"

Agent 继续改……再改……再改……

你已经记不清改了什么、为什么改

线上出了问题——没人说得清是哪次改动炸的

**结果：花了几个小时，没信心，不可复现**

</td>
<td>

你说："帮我优化一下这个 prompt"

Agent 先冻结任务定义，请你确认（Gate A）

Agent 分别写目标 prompt 和独立的机评 prompt（Gate B & C）

Agent 跑批量评估，每轮改动有指标、有日志

每一轮迭代有假设、有 diff、有分数变化

最终候选版附带完整报告——你审批上线或打回（Gate E）

**结果：有版本、有指标、可审计、可上线**

</td>
</tr>
</table>

---

## 到底强在哪

| 维度 | 裸 Agent | + 这个 Skill |
|------|---------|-------------|
| **流程** | 聊天式来回对话 | 8 阶段流水线 + 5 个人类闸门 |
| **评估** | "我看着还行" | 独立机评 prompt + 结构化打分 |
| **迭代** | 随缘修改 | 假设驱动，有 diff，有预期影响 |
| **追踪** | 翻聊天记录 | 实验日志：每轮版本、指标、成本 |
| **成本** | 花了多少不知道 | TPM/RPM 感知，默认最多 2 轮高成本迭代 |
| **失败分析** | "有时候会出错" | 11 类失败分类 + 自动聚类 |
| **交付物** | 聊天框里一段 prompt | 9 份工程制品：规格、prompt、脚本、报告 |
| **上线信心** | "Agent 说效果不错" | 有指标支撑的推荐 + 已知失败模式 |

---

## 工作流程

```
Phase 0          Phase 1            Phase 2            Phase 3
任务定义    -->   目标 Prompt   -->   机评 Prompt   -->   评估方案
  |                 |                   |                  |
Gate A            Gate B              Gate C               |
确认               确认                确认                 v
任务理解            方向正确            评估公平          Phase 4-6
                                                     生成 + 评估
                                                          |
                                                        Gate D
                                                      批准预算
                                                          |
                                                       Phase 7
                                                     分析 + 迭代
                                                          |
                                                       Phase 8
                                                      最终推荐
                                                          |
                                                        Gate E
                                                      上线验收
```

**你在闸门处把关，其余全部由 Agent 自动执行。**

---

## 核心特性

- **关注点分离** — 目标 prompt 和机评 prompt 独立开发、独立版本管理，收益不混淆。
- **假设驱动** — 每轮必须声明预期改善什么、可能退化什么，杜绝"改改试试"。
- **完整实验日志** — 版本号、改动内容、假设、指标、成本、结论——每一轮自动记录。
- **预算守卫** — 默认最多 2 轮高成本优化，收益平台期自动停止，花钱前必须人工批准。
- **失败分类体系** — 11 大类：任务理解错误、推理错误、幻觉、格式问题、约束违反等。
- **双模式** — *仅设计模式*（无需 API，输出草案和方案）或 *执行模式*（端到端真实调用模型）。

---

## 产出物

| 类别 | 文件 |
|------|------|
| 规格文档 | `docs/task_spec.md`、`docs/eval_plan.md` |
| Prompt | `prompts/production_prompt_v{n}.md`、`prompts/judge_prompt_v{n}.md` |
| 脚本 | `scripts/run_generation.py`、`scripts/run_judge.py` |
| 报告 | `reports/iteration_{n}_summary.md`、`reports/final_recommendation.md`、`reports/experiment_log.md` |

---

## 快速开始

### 安装

```bash
claude skill install abysscat-yj/prompt-design-tuning-skill
```

### 触发方式

对 Claude Code 说：

- *"帮我把这个 prompt 调优流程自动化"*
- *"先写目标 prompt，再写机评 prompt，再设计评估"*
- *"根据评估集和几个模型，找出当前最优 prompt"*
- *"控制预算做 1-2 轮 prompt 迭代"*
- *"让 agent 自动推进，人只在关键节点确认"*

---

## 许可证

MIT
