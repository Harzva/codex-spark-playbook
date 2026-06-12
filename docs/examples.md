# Examples

Use Spark for small, non-multimodal, text-only tasks with clear, auditable scope.

## Good Task

```text
Fix one typo and add one short clarifying sentence in docs/usage.md.
Do not edit source files.
Return:
- exact file changed
- concise diff summary
- quick verification steps
```

Why it works:

- Text-only work.
- Small blast radius.
- Easy to audit and review.

Example Spark output:

```text
Spark Usage Report
- model: gpt-5.3-codex-spark
- files_touched:
  - docs/usage.md
- verification:
  - sed -n '1,120p' docs/usage.md
  - rg "clarify" docs/usage.md
- token_usage:
  - input_tokens: 332
  - output_tokens: 97
  - total_tokens: 429
- token_saving_evidence: The parent session avoided spending context on a small docs-only edit.
```

If token usage is not exposed by the runtime:

```text
Spark Usage Report
- model: gpt-5.3-codex-spark
- files_touched:
  - docs/usage.md
- verification:
  - recommended: review docs/usage.md diff
- token_usage:
  - input_tokens: token_usage_unavailable
  - output_tokens: token_usage_unavailable
  - total_tokens: token_usage_unavailable
- token_saving_evidence: The bounded edit was delegated away from the parent Codex session.
```

## Good Task

```text
Write a short, neutral changelog paragraph from the provided bug-fix notes.
Limit output to plain text under 120 words.
```

Why it works:

- Text-only.
- Bounded by explicit input.
- Result is deterministic and auditable.

## Bad Task

```text
Inspect screenshots from an emulator, diagnose the bug, and propose layout changes.
```

Why it fails:

- Spark is not for screenshots or emulator/device QA.

## Bad Task

```text
Publish the release package, generate assets, and mark final acceptance as done.
```

Why it fails:

- Publishing and final acceptance stay in the parent Codex session.

## Bad Task

```text
Rotate API keys and patch the deployment secret store.
```

Why it fails:

- Secrets handling is a parent-session responsibility.

## Bad Task

```text
Design a full architecture for multi-platform event ingestion and rewrite the main backend contracts.
```

Why it fails:

- Large architecture work exceeds Spark’s small-task boundary.
