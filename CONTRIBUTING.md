# Contributing

The policy itself lives in `index.md` and is published via GitHub Pages. When it changes, update the **Last updated** date at the top.

## Entire setup

This repo tracks agent sessions with [Entire](https://docs.entire.io). The shared configuration is committed (`.entire/settings.json`, `.claude/settings.json`, `.cursor/hooks.json`), but Git hooks live in `.git/hooks`, which Git does not clone. Run this once per machine:

```bash
brew install --cask entire
entire login
entire enable -y
```

Hooks are installed for Claude Code and Cursor. For any other agent, run `entire agent add <name>` (see `entire agent list`).

This repository is public, and checkpoint data includes session prompts and transcripts. Anything captured here becomes publicly visible once pushed.
