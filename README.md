# receipts 🧾

**Your coding agent says "Done ✅". It never ran the code.**

`receipts` is a set of agent skills that make Claude Code, Codex, Cursor, and friends **show proof** before they claim anything.

## Before / after

**Without receipts**

> I've updated the date parser to handle ISO week formats. This should work now. Done ✅

**With receipts**

> Done. Receipt:
> ```
> $ pytest tests/test_dates.py
> 7 passed in 0.38s
> ```

or, when it can't check:

> Changed `parse_date` to accept ISO weeks. **Not verified**: no test runner is set up here.
> To check: `python -c "from app.dates import parse_date; print(parse_date('2026-W40'))"`

## The skills

| Skill | Stops your agent from |
|---|---|
| [`prove-it`](skills/prove-it/SKILL.md) | Saying "done", "fixed", or "all tests pass" without running anything |
| [`no-guessing`](skills/no-guessing/SKILL.md) | Inventing function names, CLI flags, and config keys from memory |
| [`repro-first`](skills/repro-first/SKILL.md) | "Fixing" bugs it never saw fail |

## Install

**Claude Code**

```
/plugin marketplace add effectustasi/receipts
/plugin install receipts@receipts
```

**Any other agent** (Codex, Cursor, Copilot, Gemini CLI, OpenCode…)

Copy the skill folders into your agent's skills directory, or paste the body of each `SKILL.md` into your `AGENTS.md` or rules file.
Per-agent guides are welcome: see [CONTRIBUTING](CONTRIBUTING.md).

## Benchmark

Coming soon: the same task set run with and without `receipts`, measuring how often the agent claims success that isn't real.
Want to help build it? Check the issues labeled `benchmark`.

## Contributing

New skills, translations, install guides for other agents, and benchmark tasks are all welcome. Start with [CONTRIBUTING.md](CONTRIBUTING.md) and the `good first issue` label.

## License

MIT
