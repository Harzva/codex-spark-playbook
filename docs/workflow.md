# Workflow

This workflow treats Spark as a secondary execution channel, not as the final decision maker.

## 1. Pick a Bounded Task

Good tasks have a tight scope:

- "Add one validation branch."
- "Write a README section from these facts."
- "Draft a unit test for this helper."
- "Review this small diff for obvious regressions."

Bad tasks are broad or irreversible:

- "Redesign the whole product."
- "Publish this repository."
- "Delete unused files."
- "Infer what is happening in these screenshots."

## 2. Sanitize Context

Before delegation, remove:

- Local credential paths.
- API keys and tokens.
- Raw terminal logs that include private data.
- Customer, reviewer, or account-specific information.

## 3. Require Evidence

Ask Spark to return:

- What changed.
- Which files were touched.
- What checks were run.
- What remains risky or unverified.

## 4. Review in Codex

The current Codex session should inspect the diff, run relevant checks, and decide whether to accept, edit, or reject the output.

Spark is useful for throughput. Codex remains responsible for correctness.
