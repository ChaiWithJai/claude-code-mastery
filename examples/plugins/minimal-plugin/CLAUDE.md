# Minimal Plugin

A template plugin demonstrating Claude Code plugin structure.

## What This Plugin Does

This is a minimal example showing:
- Plugin directory structure
- CLAUDE.md for project documentation
- Basic skill, agent, and command

## Structure

```
minimal-plugin/
├── .claude-plugin/
│   └── plugin.json      # Plugin manifest
├── CLAUDE.md            # This file
├── skills/
│   └── example/
│       └── SKILL.md     # Example skill
├── agents/
│   └── example-agent.md # Example agent
├── commands/
│   └── hello.md         # Example command
└── setup.sh             # Setup script (optional)
```

## Usage

1. Clone or copy this plugin
2. Customize the skills, agents, commands
3. Update plugin.json with your info
4. Use in your project

## Development

To test this plugin:
```bash
cd minimal-plugin
claude
> /hello
```
