---
name: hello
description: A simple hello command demonstrating command structure
argument-hint: "[optional: name]"
---

# Hello Command

A simple command to demonstrate the command structure.

## Usage

```bash
/hello           # Says hello
/hello World     # Says hello to World
```

## Output

```
Hello, [name or "there"]! 👋

This is an example command from the minimal-plugin.
```

## Notes

- Commands are triggered with `/command-name`
- Arguments are passed after the command name
- Use `argument-hint` to show expected arguments
