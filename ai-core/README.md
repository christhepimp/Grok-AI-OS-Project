# AI Core

This is where the brain of the future OS will live.

## Near-term goals

1. A simple agent that can run inside the rooted emulator (Termux or native).
2. Ability to execute shell commands, read/write files, and query system state.
3. Conversational loop that accepts natural language goals and turns them into actions.
4. Logging of every decision so we can later train or refine the system.

## Future

The code here will gradually take over more and more responsibilities that currently belong to `init`, `system_server`, package manager, etc., until the AI is the primary decision-making layer of the OS.

Start small. Stay reversible. Document everything.
