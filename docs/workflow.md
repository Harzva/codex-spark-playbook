# Workflow

This workflow treats Spark as a secondary execution channel, not as the final decision maker.

## 1. Pick a Bounded Task

Good tasks are small, non-multimodal, and easy for the parent Codex session to audit:

- "Add one validation branch."
- "Write a README section from these facts."
- "Draft a unit test for this helper."
- "Review this small diff for obvious regressions."
- "Apply this naming change in exactly these two files."

Bad tasks are broad or irreversible:

- "Redesign the whole product."
- "Publish this repository."
- "Delete unused files."
- "Infer what is happening in these screenshots."
- "Install the app on an emulator and judge whether the UI is correct."

## 2. Write Bounded Task Detail

Before delegation, write the task as a small contract:

- `task`: one precise task.
- `allowed_files`: exact files or modules Spark may touch.
- `behavior_limits`: allowed behavior changes.
- `forbidden_actions`: unrelated edits, secrets, publishing, destructive commands, multimodal assumptions.
- `expected_output`: summary, files touched, verification, risks, and usage report.
- `verification`: commands to run or recommend.
- `risks`: edge cases and assumptions to report.

## 3. Sanitize Context

Before delegation, remove:

- Local credential paths.
- API keys and tokens.
- Raw terminal logs that include private data.
- Customer, reviewer, or account-specific information.
- Screenshots, videos, and visual evidence that Spark cannot inspect reliably.

## 4. Require Evidence

Ask Spark to return:

- What changed.
- Which files were touched.
- What checks were run.
- What remains risky or unverified.
- Which model was used.
- Exact token usage if the runtime exposes it.
- `token_usage_unavailable` when token usage is not exposed.
- Token-saving evidence: what narrow work stayed out of the parent session.

## 5. Review in Codex

The current Codex session should inspect the diff, run relevant checks, and decide whether to accept, edit, or reject the output.

Spark is useful for throughput. Codex remains responsible for correctness.
