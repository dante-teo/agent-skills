# Agent Skills

A collection of reusable skills for AI coding agents, installable with the
[Skills CLI](https://github.com/vercel-labs/skills).

## Available skills

### `boy-scout`

Improves your current uncommitted code and its immediate call chain while
preserving behavior and unrelated work. It applies proportional refactoring,
keeps tests and documentation aligned, and verifies the resulting changes.

This skill runs only when you explicitly ask your agent to use it.

## Installation

The Skills CLI requires Node.js 18 or newer. You do not need to install the CLI
globally; run it with `npx`.

Install `boy-scout` in the current project:

```sh
npx skills add dante-teo/agent-skills --skill boy-scout
```

The CLI will prompt you to choose which supported agent or agents should receive
the skill.

To make the skill available across all of your projects, add `--global`:

```sh
npx skills add dante-teo/agent-skills --skill boy-scout --global
```

You can also select an agent directly. For example, to install it for Codex:

```sh
npx skills add dante-teo/agent-skills --skill boy-scout --agent codex
```

Add `--yes` to any install command to accept the default choices without
interactive prompts.

## Usage

After making code changes, explicitly ask your coding agent to apply the skill.
For example:

```text
Use the boy-scout skill to review and improve my current uncommitted changes.
```

The skill starts from the current Git diff, follows only the directly affected
call chain, and performs cleanup that can be verified without broadening the
task into an unrelated redesign.

## Managing the skill

Check whether installed skills have updates:

```sh
npx skills check
```

Update installed skills:

```sh
npx skills update
```

Remove the project-scoped installation:

```sh
npx skills remove boy-scout
```

For a global installation, include `--global` when removing it:

```sh
npx skills remove boy-scout --global
```

For all commands and supported agents, see the
[Skills CLI documentation](https://github.com/vercel-labs/skills#readme).
