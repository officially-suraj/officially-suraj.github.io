---
layout: post
title: tmux Begineer's guide
date: 2026-07-20 08:00:00 +0530
categories: linux terminal
tags:
  - tmux
  - linux
  - terminal
  - productivity
image:
  path: /assets/img/tmux-logo.png
  alt: tmux-logo
---

tmux is terminal multiplexer which runs inside your terminal and allows you to run and manage multiple terminal sessions from a single terminal window simultaneously. It is a very useful tool for anyone who interacts with a terminal on daily basis.

One of tmux's biggest advantages is that you can detach from a session, close your terminal, and your programs will continue running in the background. You can reconnect and resume exactly where you left off. This very useful feature of tmux when you're working on a remote server over SSH. If your internet connection drops, your running process will continue inside tmux. Simply reattach to your session resume your work from there.

## Installation

Most Linux distributions provide tmux through their package manager (Outdated, but okay). Alternatively, You can install it using Homebrew for Linux and macOS. To install tmux on a Windows machine use Windows Subsystem for Linux (WSL), or follow the official [tmux installation](https://github.com/tmux/tmux/wiki/Installing) guide.

I am on a Debian-based distro, I can install it using:

```bash
apt install tmux
```

## Getting started with tmux

To start a new tmux session:

```bash
tmux
```

This creates a session named `0` containing one window and one pane.

You can tell whether you're inside tmux by a green status bar appearing in the bottom of your terminal.

Try running a long program:

```bash
ping google.com
```

To detach from the session without stopping the programs, press `Ctrl + b`(prefix key) followed by `d`(hot key). `C-b` that stands for `Ctrl + b` is default prefix key, which can be changed.

To list all running sessions

```bash
tmux ls
```

At this point you can close your terminal and program will continue running.

To reattach:

```bash
tmux a
```

This will attach you to the last active session and you still see the program is running, to stop the program press `Ctrl + C`.

### Sessions, Windows, and Panes

Understanding these three concepts is key to using tmux effectively. Every session in tmux will have a window and every window will have a pane. You can create as many windows you need, and split a single pane vertically and horizontally as many times you like (until your screen allows). Sessions do not have index they do have name, which must be unique. Windows are indexed `(0)` so, you can name two windows exactly same.

### Sessions

A session is an independent workspace.

Create a named session:

```bash
tmux new -s bob
```

- Rename the current session: `Ctrl + b` then `$`.

Attach to a specific session:

```bash
tmux attach -t bob
```

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

This is where all the programs will be running.

A window always contain at least one pane.

- Split vertically active pane: `Ctrl + b` then `%`
- Split horizontally active pane: `Ctrl + b` then `"`
- Show pane numbers: `Ctrl + b` then `q`
- Move between panes: `Ctrl + b` then `Arrow Keys`
- Resize panes: `Ctrl + b` then `Ctrl + Arrow Keys`
- Close a pane: `Ctrl + b` then `x`

## Killing tmux

Kill the entire tmux server:

```bash
tmux kil-server
```

Or, if tmux becomes unresponsive:

```bash
pkill -f tmux
```

## Status line

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
| Split pane horizontally           | `Ctrl + b`, then `"`                 |
| Split pane vertically             | `Ctrl + b`, then `%`                 |
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

## Summary

We've covered the basics you'll need to get started with tmux.

As you become more comfortable with it, you'll find it can significantly improve your productivity.

Once you're comfortable with the basics, you can explore tmux plugins, copy mode, and custom key bindings, tmux can be customized extensively through `.tmux.conf` configuration file.

I would highly recommend you do check out these resources:

- [tmux Official Documentation](https://github.com/tmux/tmux/wiki/Getting-Started)
- Fireship — [tmux in 100 seconds](https://www.youtube.com/watch?v=vtB1J_zCv8I)
- NetworkChuck's — [tmux Guide](https://www.youtube.com/watch?v=nTqu6w2wc68)
- [tmuxcheatsheet.com](https://tmuxcheatsheet.com/)

Happy multiplexing!
