<p align="center">
  <img src="./docs/readme-assets/logo.svg" alt="codex-spark-playbook logo" width="220" />
</p>

<h1 align="center">codex-spark-playbook</h1>

<p align="center">
  <strong>把 codex-5.3-Spark 当成快速、可审计的小任务执行通道，而不是最终决策者。</strong>
</p>

<p align="center">
  <a href="./prompts/spark-bounded-task.md">Bounded Task Prompt</a>
  ·
  <a href="./docs/workflow.md">Workflow</a>
  ·
  <a href="./docs/limitations.md">Limitations</a>
  ·
  <a href="./docs/examples.md">Examples</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-playbook-2563eb" alt="status: playbook" />
  <img src="https://img.shields.io/badge/focus-bounded%20tasks-0f172a" alt="focus: bounded tasks" />
  <img src="https://img.shields.io/badge/model-codex--spark-facc15" alt="model: codex spark" />
  <img src="https://img.shields.io/badge/license-MIT-22c55e" alt="license: MIT" />
</p>

> This is not an unlimited quota claim. It is a practical workflow based on current account UI observations: Spark appears to be counted separately from 5.4 / 5.5 usage, and it is useful when the task is narrow enough for Codex to review afterward.

## What It Solves

High-value model context should not be spent on every small implementation detail. This playbook gives you a repeatable way to delegate narrow text-only tasks to Spark, then bring the output back to the current Codex session for review.

| Use Spark For | Keep In Codex |
| --- | --- |
| Small patches with a narrow file scope | Final acceptance and release decisions |
| Prompt, README, test, and checklist drafts | Secrets, publishing, deletion, migrations |
| Local refactors with reviewable diffs | Multimodal work such as images and screenshots |
| Second-pass analysis when main quota is tight | Ambiguous product direction or large redesigns |

## 30-Second Workflow

```mermaid
flowchart LR
    A["Codex defines a bounded task"] --> B["Spark drafts the result"]
    B --> C["Codex reviews diff and evidence"]
    C --> D{"Accept?"}
    D -->|yes| E["Commit or continue"]
    D -->|no| F["Revise or reject"]
```

The rule is simple:

```text
Codex plans the bounded task.
Spark drafts the result.
Codex reviews the diff, evidence, and tests.
Only Codex accepts or rejects the result.
```

## Quick Start

1. Open [`prompts/spark-bounded-task.md`](./prompts/spark-bounded-task.md).
2. Replace the task, allowed files, behavior, and checks.
3. Keep the context small and sanitized.
4. Ask Spark for summary, touched files, verification, risks, and assumptions.
5. Review the result in the current Codex session before accepting anything.

## Safety Boundaries

- Do not pass secrets, tokens, cookies, private account files, or raw credential logs.
- Do not ask Spark to publish, delete, push, migrate, or perform irreversible actions.
- Do not use Spark for image, screenshot, video, visual UI, or diagram interpretation.
- Do not describe Spark as free, unlimited, official, or guaranteed to bypass quota limits.

## Repository Map

| Path | Purpose |
| --- | --- |
| [`prompts/spark-bounded-task.md`](./prompts/spark-bounded-task.md) | Default delegation prompt for small reviewable tasks |
| [`docs/workflow.md`](./docs/workflow.md) | Step-by-step operating workflow |
| [`docs/limitations.md`](./docs/limitations.md) | Quota wording, multimodal limits, and public safety notes |
| [`docs/examples.md`](./docs/examples.md) | Good and bad delegation examples |

## When This Is Worth Using

Use this playbook when you already know the next step and want a fast draft. Avoid it when the problem is still unclear, visual, sensitive, or release-critical.

Spark is useful for throughput. Codex remains responsible for correctness.
