---
name: prove-it
description: Use before telling the user that any task is done, fixed, working, passing, or deployed. Requires fresh evidence from this session (command output, test results, a screenshot of the running app) before claiming success, and an explicit "not verified" when there is none. Triggers when finishing any coding task, or before writing "done", "fixed", "works", "should work", "all tests pass".
---

# Prove it

You may not say a task is done, fixed, or working unless you have a **receipt** from this session.

## What counts as a receipt

- Output of a command you ran **after your last edit**: the tests, the build, the type checker, the script itself.
- For UI changes: a screenshot or DOM read of the running app showing the change.
- For a bug fix: the original reproduction now behaving correctly.

What does **not** count:

- "The code looks right."
- Tests you did not run, or ran before your last edit.
- A passing test that never executes the code you changed.
- Reasoning about what the output *would* be.

## The rule

1. After your last edit, run the smallest check that would **fail if your change were wrong**.
2. Read the output. Exit code, failures, and warnings that touch your change. Not just the last line.
3. Report with the receipt: the command and the lines that prove it.
4. If you cannot verify (no test environment, needs credentials, needs hardware, would take hours), say exactly that. Never round "unverified" up to "done".

## Report format

Verified:

````
Done. Receipt:
```
$ pytest tests/test_auth.py
5 passed in 0.41s
```
````

Not verified:

```
Changed `parse_date` to accept ISO weeks. **Not verified**: no test runner is set up here.
To check: `python -c "from app.dates import parse_date; print(parse_date('2026-W40'))"`
```

## Phrases you may not use without a receipt

"should work", "this fixes it", "all tests pass", "verified", "confirmed", "Done ✅", "works now".

## Edge cases

- **Check failed?** Say so first and show the failure. Do not bury it under a summary of what you changed.
- **Failures unrelated to your change?** Name them. Only call them pre-existing if you showed they fail without your change too (for example with `git stash`); otherwise say you did not check.
- **Partial verification?** Say which part is proven and which is not.
- **Never** write a test that passes trivially just to have a receipt. The check has to exercise the change.
