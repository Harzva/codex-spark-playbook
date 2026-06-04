# codex-spark-playbook

A bounded-task playbook for using Codex Spark as a fast secondary execution channel.

Codex Spark is useful when the task is small, well-scoped, and easy for the current Codex session to review afterward. The key observation behind this playbook is practical rather than official: in the current account UI, Spark appears to have a usage bucket that is separate from 5.4 / 5.5 model usage. Treat that as an observed account behavior, not a guarantee.

## Use Spark For

- Small code patches with a narrow file scope.
- Drafting implementation plans from already-sanitized context.
- Local refactors where the expected diff can be reviewed quickly.
- Tests, examples, docs, and checklist drafts.
- Second-pass analysis when the main model quota is tight.

## Do Not Use Spark For

- Multimodal work: images, screenshots, UI visual review, video, or diagrams.
- Secrets, tokens, credentials, cookies, or private account data.
- Destructive actions, publishing, deletion, migrations, or irreversible changes.
- Large ambiguous product decisions.
- Final acceptance. The current Codex session must review Spark output.

## Operating Rule

```text
Codex plans the bounded task.
Spark drafts the result.
Codex reviews the diff, evidence, and tests.
Only Codex accepts or rejects the result.
```

## Quick Prompt

Use `prompts/spark-bounded-task.md` as the default handoff prompt. Keep the input small, name the exact files or behaviors, and require a concise result with risks and verification steps.

## Why This Exists

Spark is not positioned here as a stronger model. It is positioned as a fast secondary worker for narrow tasks. That makes it useful when you want progress without spending the highest-value model context on every small implementation detail.

## Limitations

See `docs/limitations.md` before using this workflow in public repos or client work.
