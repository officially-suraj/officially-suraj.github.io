---
layout: post
title: "tmux Guide: Manage terminal sessions like a pro!"
date: 2026-07-18
categories: linux terminal
tags:
  - tmux
  - linux
  - terminal
  - productivity
image:
  path: /assets/img/tmux-logo.png
  lqip:
  alt: tmux-logo
---

tmux is a terminal multiplexer, that runs inside your terminal and allows you to manage multiple terminal sessions from a single terminal window.
It is an incredibly useful tool for anyone who works in the terminal regularly.

One of tmux's biggest advantages is that you can detach from a session, close your terminal, and your programs will continue running in the background.
Later, you can reconnect and resume exactly where you left off.

This is especially useful when working on a remote server over SSH. If
your internet connection drops, your running processes will continue
uninterrupted inside tmux. Simply reconnect and reattach to your
session.

Its scriptability and customizability have made tmux a famous tool among developers and system administrators.

## Installation

Most Linux distributions provide tmux through their package manager. On macOS, you can install it using Homebrew. Windows users can install it through the Windows Subsystem for Linux (WSL), or follow the official [installation guide]().

On Debian-based distributions:

```bash
apt install tmux
```

## Starting with tmux

Start a new tmux session:

```bash
tmux
```

This creates a session named `0` containing one window and one pane.

You can recognize that you're inside tmux by the green status line displayed at the bottom of the terminal.

Try printing a simple message:

```bash
echo "Hello, World!"
```

To detach from the session without stopping your programs, press:

`Ctrl + b` followed by `d`

To list all running sessions:

```bash
tmux ls
```

To reattach to the most recently used session:

```bash
tmux attach
```

You should still see the output you left behind.

## Sessions, Windows, and Panes

Understanding these three concepts is the key to using tmux effectively.

### Sessions

A session is an independent workspace.

Create a named session:

```bash
tmux new -s bob
```

Attach to a specific session:

```bash
tmux attach -t bob
```

Rename the current session with:

`Ctrl + b` then `$`

Close a session:

```bash
tmux kill-session
```

### Windows

A session can contain multiple windows.

- Create a new window: `Ctrl + b` then `c`
- Rename a window: `Ctrl + b` then `,`
- Next window: `Ctrl + b` then `n`
- Previous window: `Ctrl + b` then `p`
- Close a window: `Ctrl + b` then `&`

### Panes

A window always contains at least one pane.

Split vertically:

`Ctrl + b` then `"`

Split horizontally:

`Ctrl + b` then `%`

Move between panes:

`Ctrl + b` then `Arrow Keys`

Show pane numbers:

`Ctrl + b` then `q`

Resize panes:

`Ctrl + b` then `Ctrl + Arrow Keys`

Close the active pane:

`Ctrl + b` then `x`

## Killing tmux

Kill the entire tmux server:

```bash
tmux kill-server
```

Or, if tmux becomes unresponsive:

```bash
pkill -f tmux
```

## Status Line

The green status line displays useful information such as:

- Current session
- Current window
- Active window
- Hostname
- Date and time

Example:

```text
[0] 0:bash*    "user"    HH:MM DD-Month-YY
```

## Summary

We've covered the basics you'll need to get started with tmux. As you become more comfortable with it, you'll find it can significantly improve your productivity.

## tmux Cheatsheet

| Action                            | Command / Shortcut                   |
| --------------------------------- | ------------------------------------ |
| Create session                    | `tmux`                               |
| Create named session              | `tmux new -s <name>`                 |
| List sessions                     | `tmux ls`                            |
| Attach to the last active session | `tmux attach`                        |
| Attach to a named session         | `tmux attach -t <name>`              |
| Kill the current session          | `tmux kill-session`                  |
| Kill a named session              | `tmux kill-session -t <name>`        |
| Kill the tmux server              | `tmux kill-server`                   |
| Detach from the current session   | `Ctrl + b`, then `d`                 |
| Split pane horizontally           | `Ctrl + b`, then `%`                 |
| Split pane vertically             | `Ctrl + b`, then `"`                 |
| Create a new window               | `Ctrl + b`, then `c`                 |
| Rename the current window         | `Ctrl + b`, then `,`                 |
| Switch to the next window         | `Ctrl + b`, then `n`                 |
| Switch to the previous window     | `Ctrl + b`, then `p`                 |
| Switch between panes              | `Ctrl + b`, then `Arrow Keys`        |
| Show pane numbers                 | `Ctrl + b`, then `q`                 |
| Resize panes                      | `Ctrl + b`, then `Ctrl + Arrow Keys` |
| Rename the current session        | `Ctrl + b`, then `$`                 |
| Close the current pane            | `Ctrl + b`, then `x`                 |
| Close the current window          | `Ctrl + b`, then `&`                 |
| Exit the current pane/window      | `Ctrl + d` or `exit`                 |

## What Next

tmux can be customized extensively through the `.tmux.conf` configuration file. Once you're comfortable with the basics, explore plugins, copy mode, and custom key bindings.

Recommended resources:

- tmux Official Documentation
- Fireship — [tmux in 100 seconds](https://www.youtube.com/watch?v=vtB1J_zCv8I)
- NetworkChuck's — [tmux Guide](https://www.youtube.com/watch?v=nTqu6w2wc68)
- [tmuxcheatsheet.com](https://tmuxcheatsheet.com/)

Happy multiplexing!
