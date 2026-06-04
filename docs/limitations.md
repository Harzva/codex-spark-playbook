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

## No Final Acceptance

Spark output is a draft. The current Codex session must review code diffs, documentation claims, and verification evidence before accepting the result.

## Public Safety

Do not publish private paths, tokens, local account names, raw logs, or unredacted screenshots in a public repository.
