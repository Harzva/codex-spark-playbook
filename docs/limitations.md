# Limitations

## Quota Claims

The separate Spark quota idea is based on current account UI observations. It may change by account, plan, region, date, or product rollout. Do not present this as an official unlimited quota.

Use careful wording:

```text
In my current account UI, Spark appears to be counted separately from 5.4 / 5.5 usage.
```

Avoid:

```text
Spark is free.
Spark is unlimited.
Spark bypasses model limits.
```

## No Multimodal Support

Do not use Spark for tasks that depend on images, screenshots, videos, visual UI inspection, or diagram interpretation.

For those tasks, use a multimodal-capable model first, then optionally pass a text-only bounded task to Spark.

## No Device Or App Interaction QA

Do not use Spark as the authority for real device, emulator, simulator, browser, or app-interaction acceptance.

Spark can draft test commands, checklists, or code changes for those workflows. The parent Codex session must perform or review the actual device/app evidence.

## No Final Acceptance

Spark output is a draft. The current Codex session must review code diffs, documentation claims, and verification evidence before accepting the result.

## Token Usage Reporting

Spark workers should report model usage after each task. If the runtime exposes exact token usage, report input, output, and total tokens.

If the runtime does not expose token usage, do not estimate. Report:

```text
token_usage_unavailable
```

Then record token-saving evidence: the small, bounded work that was delegated away from the parent Codex session.

## Public Safety

Do not publish private paths, tokens, local account names, raw logs, credential dumps, authorization transcripts, or unredacted screenshots in a public repository.
