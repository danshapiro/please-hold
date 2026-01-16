# Please Hold

Long waits and delayed execution for Claude Code.

## Why?

Claude Code's Bash tool has a 10-minute (600,000ms) maximum timeout. This skill teaches how to wait for hours or indefinitely by chaining background sleeps with task notifications.

## Use Cases

- "Wait 4 hours then remind me to check the deployment"
- "Remind me at 3pm to call the client"
- "Do this after the file contains 'ready'"
- "Do this after staging has two new versions"

## Installation

```
/plugin marketplace add danshapiro/please-hold
/plugin install please-hold@danshapiro-please-hold
```

## Usage

The skill is automatically invoked when you ask Claude to wait longer than 10 minutes or do something after a condition becomes true.

Examples:
- "Wait 2 hours then run the build"
- "At 5pm, remind me to submit the report"
- "After the CI passes, deploy to staging"

## How It Works

Background tasks create an event-driven loop:

```
sleep (background) → <task-notification> → sleep (background) → ... → execute
```

Each 10-minute sleep runs with `run_in_background: true`, returning immediately. When complete, Claude receives a `<task-notification>` and starts the next interval. Progress is tracked via TodoWrite.

## License

MIT
