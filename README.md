# Prompt Design & Tuning Skill

### Turn prompt tuning from guesswork into engineering.

> A Claude Code Skill that transforms prompt optimization into a **structured, repeatable, cost-controlled** workflow — where agents do the heavy lifting and humans stay in control at the gates that matter.

---

## The Problem

Most prompt tuning looks like this: tweak a sentence, eyeball the output, repeat until it "feels right." No versioning, no metrics, no reproducibility. When it breaks in production, nobody knows which change caused it.

## The Solution

This skill enforces an **engineering-grade prompt development lifecycle**:

```
Task Spec --> Target Prompt --> Judge Prompt --> Eval Plan --> Generate --> Evaluate --> Iterate --> Ship
    |              |                |               |                                    |         |
  Gate A         Gate B           Gate C          Gate D                                Gate D   Gate E
  (human)        (human)          (human)         (human)                               (human)  (human)
```

**The agent executes.** You only approve at the checkpoints.

---

## Key Features

**Separation of Concerns** — Target prompt and judge prompt are developed independently. No mixing gains.

**Hypothesis-Driven Iteration** — Every optimization round starts with a clear hypothesis. No "let's just tweak it and see."

**Experiment Logging** — Every round records: version, changes, hypothesis, metrics, cost, and conclusion.

**Cost Control** — Default max 2 high-cost rounds. Budget-aware. Early stopping when gains plateau.

**Failure Taxonomy** — Systematic classification: task misunderstanding, reasoning errors, hallucinations, format issues, and more.

**Two Working Modes** — *Design-only* (no API needed) or *Execution* (end-to-end automation with real model calls).

---

## Deliverables

The skill produces a complete artifact set:

| Category | Files |
|----------|-------|
| Specification | `docs/task_spec.md`, `docs/eval_plan.md` |
| Prompts | `prompts/production_prompt_v{n}.md`, `prompts/judge_prompt_v{n}.md` |
| Scripts | `scripts/run_generation.py`, `scripts/run_judge.py` |
| Reports | `reports/iteration_{n}_summary.md`, `reports/final_recommendation.md`, `reports/experiment_log.md` |

---

## Human Gates

You stay in control at 5 key checkpoints:

| Gate | Purpose |
|------|---------|
| **A** | Freeze the task definition |
| **B** | Approve target prompt direction |
| **C** | Approve judge prompt direction |
| **D** | Authorize high-cost iteration loops |
| **E** | Final launch review |

Between gates, the agent runs autonomously.

---

## Quick Start

### Install the Skill

```bash
claude skill install abysscat-yj/prompt-design-tuning-skill
```

### Trigger It

Say any of these to Claude Code:

- *"Help me design and tune this prompt"*
- *"Write the target prompt, then the judge, then run evaluation"*
- *"Find the best prompt across these models within my budget"*
- *"Run 1-2 prompt iteration rounds with cost control"*
- *"Automate this prompt tuning workflow"*

---

## Anti-Patterns (What This Skill Prevents)

- Changing both target and judge prompts in the same round without disclosure
- Looking only at aggregate scores while ignoring failure distributions
- Overfitting to tiny eval sets without warning
- Substituting machine evaluation for final human review
- Endless looping over marginal score improvements
- Full rewrites when only one section is broken
- Declaring success without showing hard examples

---

## License

MIT

---

<br>

# Prompt 设计调优 Skill

### 把 prompt 调优从玄学变成工程。

> 一个 Claude Code Skill，将 prompt 优化变成**可执行、可复盘、可控成本**的工程流程 —— Agent 负责执行，人类只在关键节点把关。

---

## 痛点

大多数 prompt 调优是这样的：改一句话，肉眼看看输出，感觉差不多就上线。没有版本管理，没有指标追踪，没有可复现性。线上出了问题，谁也说不清是哪次改动导致的。

## 解决方案

这个 Skill 强制执行一套**工程级 prompt 开发流程**：

```
任务定义 --> 目标Prompt --> 机评Prompt --> 评估方案 --> 批量生成 --> 机器评估 --> 迭代优化 --> 上线
   |            |              |            |                                   |          |
 Gate A       Gate B         Gate C       Gate D                              Gate D     Gate E
 (人工确认)    (人工确认)      (人工确认)    (人工确认)                           (人工确认)   (人工确认)
```

**Agent 负责执行，你只需要在关键检查点批准。**

---

## 核心特性

**关注点分离** — 目标 prompt 和机评 prompt 独立开发，收益不混淆。

**假设驱动迭代** — 每一轮优化都必须有明确假设，杜绝"改改试试"。

**实验记录** — 每轮记录：版本号、改动内容、优化假设、指标结果、成本、结论。

**成本控制** — 默认最多 2 轮高成本优化，预算感知，收益平台期自动停止。

**失败分类体系** — 系统化归类：任务理解错误、推理错误、幻觉、格式问题等。

**双工作模式** — *仅设计模式*（无需 API）或 *执行模式*（端到端自动化，真实调用模型）。

---

## 产出物

Skill 产出一套完整的工程制品：

| 类别 | 文件 |
|------|------|
| 规格文档 | `docs/task_spec.md`、`docs/eval_plan.md` |
| Prompt | `prompts/production_prompt_v{n}.md`、`prompts/judge_prompt_v{n}.md` |
| 脚本 | `scripts/run_generation.py`、`scripts/run_judge.py` |
| 报告 | `reports/iteration_{n}_summary.md`、`reports/final_recommendation.md`、`reports/experiment_log.md` |

---

## 人类闸门

你在 5 个关键检查点保持控制权：

| 闸门 | 用途 |
|------|------|
| **A** | 冻结任务定义 |
| **B** | 确认目标 prompt 方向 |
| **C** | 确认机评 prompt 方向 |
| **D** | 批准高成本迭代循环 |
| **E** | 最终上线验收 |

闸门之间，Agent 全自动执行。

---

## 快速开始

### 安装 Skill

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

## 反模式（这个 Skill 帮你避免的坑）

- 同一轮既改目标 prompt 又改机评 prompt，却不说明
- 只看总分，不看失败分布
- 在超小评估集上过拟合，却不提醒风险
- 用机评替代人工最终验收
- 分数微小波动就无限循环
- 一个点坏了就把整个 prompt 全部重写
- 没展示硬例子就宣布"效果很好"

---

## 许可证

MIT
