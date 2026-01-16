# Please Hold

Long waits and delayed execution for Claude Code.

## Why?

Claude Code's Bash tool has a 10-minute (600,000ms) maximum timeout. This skill teaches how to wait for hours or indefinitely by chaining background sleeps with task notifications.

## Use Cases

- "Wait until the checkin that fixes the widgets hits main, then rebase onto it, merge, and deploy"
- "Implement the spec after my tokens reset at 1am"
- "Run the live tests when the new version arrives on staging"

## Installation

```
/plugin marketplace add danshapiro/please-hold
/plugin install please-hold@danshapiro-please-hold
```

## Usage

The skill is automatically invoked when you ask Claude to wait longer than 10 minutes or do something after a condition becomes true.

Examples:
- "Wait until the checkin that fixes the widgets hits main, then rebase onto it, merge, and deploy"
- "Implement the spec after my tokens reset at 1am"
- "Run the live tests when the new version arrives on staging"

## How It Works

Background tasks create an event-driven loop:

```
sleep (background) → <task-notification> → sleep (background) → ... → execute
```

Each 10-minute sleep runs with `run_in_background: true`, returning immediately. When complete, Claude receives a `<task-notification>` and starts the next interval. Progress is tracked via TodoWrite.

## License

MIT
