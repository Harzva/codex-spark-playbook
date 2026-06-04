# Examples

## Good Task

```text
Implement only the missing validation branch in src/config.ts.
Do not touch other files.
Return the diff summary and the exact test command to run.
```

Why it works:

- The file scope is clear.
- The expected change is small.
- The parent Codex session can review the result quickly.

## Good Task

```text
Draft a README section explaining the retry policy from these sanitized facts.
Do not invent benchmark numbers or official claims.
```

Why it works:

- The input is text-only.
- The result is easy to review.
- The model is constrained against overclaiming.

## Bad Task

```text
Look at these screenshots and design the final launch image.
```

Why it fails:

- Spark should not be used for multimodal work.
- The task is visual and subjective.

## Bad Task

```text
Create the GitHub repository, publish the post, and mark everything done.
```

Why it fails:

- Publishing is irreversible.
- Final acceptance must stay with the current Codex session.
