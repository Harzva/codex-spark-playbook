---
name: cxspark
description: Codex Spark shortcut skill for delegating small, bounded, non-multimodal coding, docs, README, prompt, checklist, review, or mechanical-edit tasks to a Spark sub-agent using gpt-5.3-codex-spark. Use when the user says cxspark, cx spark, Codex Spark shortcut, or asks to run a narrow task through Spark while the parent Codex session keeps planning, review, verification, publishing, and dangerous operations.
---

# cxspark

`cxspark` means "Codex Spark". Use it as a short trigger for bounded Spark delegation. Treat Spark as a fast draft worker. The parent Codex session remains responsible for planning, reviewing diffs, running checks, accepting results, commits, pushes, releases, and any risky operation.

`cxspark` is a fixed work role, not a fixed agent identity. Each task may spawn a temporary Spark worker with a different runtime name, but the job definition, task boundary, allowed scope, and reporting contract stay stable.

## Use Spark For

- Small code patches with narrow file ownership.
- README, docs, prompt, checklist, or task-bank drafts.
- Single-file or few-file mechanical edits.
- Text-only review of a small diff or decision.

## Keep In Parent Codex

- Secrets, tokens, cookies, credential files, or raw private logs.
- Publishing, pushing, deleting, migrations, resets, or irreversible actions.
- Screenshots, images, videos, visual UI inspection, browser QA, emulator QA, device QA, or app-interaction acceptance.
- Broad architecture, product direction, final release acceptance, and high-risk decisions.

## Delegation

When the user asks to use `cxspark`, delegate only if the task is bounded and safe. Spawn a sub-agent with:

- `agent_type`: `worker` for implementation or `explorer` for read-only codebase questions.
- `model`: `gpt-5.3-codex-spark`.
- `fork_context`: `false` unless the task genuinely needs full parent context.

Give Spark a sanitized bounded task. Do not include secrets or large unrelated history.

## Bounded Task Detail

Use this handoff shape:

```text
Task:
<one precise task>

Allowed scope:
- Files: <exact files or modules>
- Behavior limits: <allowed behavior changes>
- Tests or checks: <required checks>

Forbidden actions:
- Change unrelated files.
- Read or output secrets, tokens, cookies, private account data, or raw credentials.
- Publish, delete, push, migrate, reset, or perform irreversible actions.
- Perform image, screenshot, video, browser, emulator, simulator, device, or app-interaction QA.
- Mark work final.

Expected output:
1. Summary of changes.
2. Files touched.
3. Verification performed or recommended.
4. Risks, edge cases, and assumptions.
5. Spark Usage Report.
```

## Spark Usage Report

Every Spark result must report:

```text
Spark Usage Report:
- model: gpt-5.3-codex-spark
- task: <short task summary>
- files_touched: <paths or none>
- verification: <performed or recommended>
- token_usage:
  - input_tokens: <number or token_usage_unavailable>
  - output_tokens: <number or token_usage_unavailable>
  - total_tokens: <number or token_usage_unavailable>
- token_saving_evidence: <what parent-session context/work was avoided>
```

If exact token usage is unavailable, report `token_usage_unavailable`; never invent numbers.

## Acceptance

After Spark returns, inspect its result locally before accepting it. Run the relevant checks in the parent session. Spark output is a draft, not the final answer.
