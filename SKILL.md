---
name: codex-spark-playbook
description: Delegate small, bounded, non-multimodal implementation, review, README, docs, prompt, checklist, and mechanical-edit subtasks to codex-5.3-spark / gpt-5.3-codex-spark while keeping planning, final review, release decisions, publishing, device QA, visual inspection, and dangerous operations in the parent Codex session.
---

# Codex Spark Playbook

Use this skill when the user asks to use Spark, codex-5.3-spark, gpt-5.3-codex-spark, a fast secondary Codex worker, or this playbook for a narrow task.

Spark is a bounded draft worker. The parent Codex session remains responsible for planning, reviewing diffs, running required checks, and accepting or rejecting the result.

For a short portable trigger, install or reference [`skills/cxspark/SKILL.md`](skills/cxspark/SKILL.md). `cxspark` is the fixed role name for the same bounded-worker pattern; individual worker instances may still be temporary.

## Fit Check

Use Spark for:

- Small code patches with exact file ownership.
- README, docs, prompt, checklist, and test drafts.
- Single-file or few-file mechanical edits.
- Text-only second-pass review of a small diff or decision.
- Non-multimodal work that the parent session can audit quickly.

Keep work in the parent Codex session for:

- Images, screenshots, video, visual UI judgment, or diagram interpretation.
- Real device, emulator, simulator, browser, or app-interaction QA.
- Secrets, tokens, cookies, private account data, or raw credential logs.
- Publishing, pushing, deleting, migrations, resets, or irreversible actions.
- Broad architecture, product direction, release acceptance, or final sign-off.

## Delegation Procedure

Before spawning Spark, write a bounded task detail:

- `task`: one precise task.
- `allowed_files`: exact files or modules Spark may touch.
- `behavior_limits`: allowed behavior changes.
- `forbidden_actions`: unrelated edits, secrets, publishing, destructive commands, multimodal assumptions.
- `expected_output`: summary, touched files, verification, risks, and usage report.
- `verification`: commands to run or recommend.
- `risks`: edge cases and assumptions to report back.

If a sub-agent tool is available and delegation is appropriate, spawn Spark with:

- `agent_type`: `worker` for implementation, `explorer` for read-only code questions.
- `model`: `gpt-5.3-codex-spark`.
- `fork_context`: `false` unless the task genuinely needs the parent context.

Tell the worker it is not alone in the codebase, must not revert others' work, and must keep edits inside the allowed scope.

## Spark Usage Report

Every Spark result must include a usage report:

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
- token_saving_evidence: <what main-session context/work was avoided>
```

If runtime token usage is unavailable, do not estimate or invent numbers. Report `token_usage_unavailable` and describe the bounded work that was kept out of the main session as token-saving evidence.

## Review Rule

Treat Spark output as a draft. The parent Codex session must inspect the diff, check public-safety boundaries, run relevant validation, and decide whether to accept, edit, or reject the result.

Use `prompts/spark-bounded-task.md` as the default handoff template. Read `docs/workflow.md`, `docs/limitations.md`, and `docs/examples.md` when a task needs more detailed operating guidance.
