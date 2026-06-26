# sunrise

Set the time your Claude **5-hour usage window** starts each day — so resets land when you want them, not whenever you happen to start working.

```
/sunrise:set 9am
```

This creates a tiny **cloud routine** on your account that pings Claude 4×/day (every 5 hours) with a no-op message. Each ping starts/refreshes your 5-hour window, keeping it primed on a schedule you choose.

## Why

Claude usage runs in 5-hour windows that begin on your first message and reset 5 hours later. Start at 9am → you reset at 2pm. By priming the window early (even while you sleep), your resets land on a predictable daily cadence and a fresh window is always ready when you sit down.

## Install

Requires a **Claude Pro or Max** plan with Claude Code routines.

```
/plugin marketplace add shaharyar1255/sunrise
/plugin install sunrise@shaharyar1255
```

## Use

```
/sunrise:set 9am
```

Pick the hour your day starts. The plugin computes a 4×/day schedule (for `9am`: 9am, 2pm, 7pm, 12am), confirms the reset times with you, then creates the routine. Re-run with a new time to change it.

## How it works

A Claude Code plugin **can't run on a timer** — its commands and hooks only fire while Claude is open. So this plugin doesn't *do* the priming itself. It sets up a **cloud routine**, which runs 24/7 on Anthropic's infrastructure even with your machine off. The routine just sends `ok` to Haiku — enough to start a window.

- 4 pings/day, 5h apart → window primed ~20h/day, with one unavoidable ~4h gap parked overnight.
- Uses ~4 of your 15 daily routine runs.
- **No GitHub repo, no OAuth token, no secrets** — it creates the routine on your own account.

## Manage / turn off

See or pause your routine at [claude.ai/code/routines](https://claude.ai/code/routines), or run `/schedule list`.

> Routines are an Anthropic research-preview feature; limits and behavior may change.

## License

MIT — see [LICENSE](LICENSE).
