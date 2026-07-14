---
layout: post
title: "tmux Beginner's Guide: Manage Multiple Terminal Sessions Like a Pro"
date: 2026-07-14
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

`tmux` is a terminal multiplexer that lets you create multiple terminal sessions inside a single window. It is an essential tool for developers, system administrators, and anyone working on remote servers.

## Why use tmux?

Without tmux:

- Closing your terminal stops running programs.
- SSH disconnections interrupt long-running tasks.
- Managing multiple terminal windows becomes cluttered.

With tmux:

- Sessions continue running even after disconnecting.
- Split the terminal into multiple panes.
- Create multiple windows inside one terminal.
- Reconnect to existing sessions anytime.

---

## Installing tmux

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install tmux
```

### Fedora

```bash
sudo dnf install tmux
```

### Arch Linux

```bash
sudo pacman -S tmux
```

Verify the installation:

```bash
tmux -V
```

---

## Starting tmux

```bash
tmux
```

Or create a named session:

```bash
tmux new -s work
```

---

## Detaching from a Session

Press:

```
Ctrl+b
```

Release both keys, then press:

```
d
```

The session continues running in the background.

---

## Listing Sessions

```bash
tmux ls
```

Example:

```text
work: 1 windows
server: 2 windows
```

---

## Reattaching

```bash
tmux attach -t work
```

---

## Creating Windows

Shortcut:

```
Ctrl+b c
```

Move between windows:

```
Ctrl+b n
Ctrl+b p
```

---

## Splitting Panes

Vertical split:

```
Ctrl+b %
```

Horizontal split:

```
Ctrl+b "
```

Navigate panes:

```
Ctrl+b ←
Ctrl+b →
Ctrl+b ↑
Ctrl+b ↓
```

---

## Renaming a Window

```
Ctrl+b ,
```

---

## Killing a Pane

Type:

```bash
exit
```

or press

```
Ctrl+d
```

---

## Killing a Session

```bash
tmux kill-session -t work
```

Kill every session:

```bash
tmux kill-server
```

---

## Useful Commands

| Task | Command |
|------|---------|
| Start tmux | `tmux` |
| New named session | `tmux new -s name` |
| List sessions | `tmux ls` |
| Attach | `tmux attach -t name` |
| Kill session | `tmux kill-session -t name` |

---

## Essential Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+b c` | New window |
| `Ctrl+b n` | Next window |
| `Ctrl+b p` | Previous window |
| `Ctrl+b %` | Vertical split |
| `Ctrl+b "` | Horizontal split |
| `Ctrl+b d` | Detach session |
| `Ctrl+b x` | Kill pane |

---

## Final Thoughts

Learning a handful of tmux commands can dramatically improve your productivity, especially when working over SSH or managing multiple development tasks. Start by creating sessions, splitting panes, and detaching safely. As you become more comfortable, you can explore custom key bindings and configuration through a `.tmux.conf` file.

Happy multiplexing!