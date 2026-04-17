---
title: IPC
description: Control xorawm programmatically using xctl.
---

## Introduction

xorawm includes a powerful IPC (Inter-Process Communication) tool called `xctl`. This allows you to query the window manager's state, watch for events, and execute commands from external scripts.

## Basic Usage

The general syntax for `xctl` is:

```bash
xctl [-OTLq]
xctl [-o <output>] -s [-t <tags>] [-l <layout>] [-c <tags>] [-d <cmd>,<arg1>,<arg2>,<arg3>,<arg4>,<arg5>]
xctl [-o <output>] (-g | -w) [-OotlcvmfxekbA]
```

### Options

| Flag | Description |
| :--- | :--- |
| `-q` | Quit xorawm. |
| `-g` | **Get** values (tags, layout, focused client). |
| `-s` | **Set** values (switch tags, layouts). |
| `-w` | **Watch** mode (streams events). |
| `-O` | Get all output (monitor) information. |
| `-T` | Get number of tags. |
| `-L` | Get all available layouts. |
| `-o` | Select output (monitor). |
| `-t` | Get/set selected tags (set with `[+-^.]`). |
| `-l` | Get/set current layout. |
| `-c` | Get title and appid of focused client. |
| `-v` | Get visibility of statusbar. |
| `-m` | Get fullscreen status. |
| `-f` | Get floating status. |
| `-d` | **Dispatch** an internal command. |
| `-x` | Get focused client geometry. |
| `-e` | Get the name of the last focused layer. |
| `-k` | Get current keyboard layout. |
| `-b` | Get current keybind mode. |
| `-A` | Get scale factor of monitor. |

## Examples

### Tag Management

You can perform arithmetic on tags using the `-t` flag with `-s` (set).

```bash
# Switch to Tag 1
xctl -t 1

# Add Tag 2 to current view (Multiview)
xctl -s -t 2+

# Remove Tag 2 from current view
xctl -s -t 2-

# Toggle Tag 2
xctl -s -t 2^
```

### Layouts

Switch layouts programmatically. Layout codes: `S` (Scroller), `T` (Tile), `G` (Grid), `M` (Monocle), `K` (Deck), `CT` (Center Tile), `RT` (Right Tile), `VS` (Vertical Scroller), `VT` (Vertical Tile), `VG` (Vertical Grid), `VK` (Vertical Deck), `TG` (TGMix).

```bash
# Switch to Scroller
xctl -l "S"

# Switch to Tile
xctl -l "T"
```

### Dispatching Commands

Any command available in `config.conf` keybindings can be run via IPC.

```bash
# Close the focused window
xctl -d killclient

# Resize window by +10 width
xctl -d resizewin,+10,0

# Toggle fullscreen
xctl -d togglefullscreen

# Disable a monitor power
xctl -d disable_monitor,eDP-1
```

### Monitoring & Status

Use `-g` or `-w` to build custom status bars or automation scripts.

```bash
# Watch for all message changes
xctl -w

# Get all messages without watch
xctl -g

# Watch focused client appid and title
xctl -w -c

# Get all available outputs
xctl -O

# Get all tags message
xctl -g -t

# Get current focused client message
xctl -g -c

# Get current keyboard layout
xctl -g -k

# Get current keybind mode
xctl -g -b

# Get scale factor of current monitor
xctl -g -A
```

#### Tag Message Format

- State: 0 → none, 1 → active, 2 → urgent

Example output:

| Monitor | Tag Number | Tag State | Clients in Tag | Focused Client |
|---------|------------|-----------|----------------|----------------|
| eDP-1   | tag 2      | 0         | 1              | 0              |

| Monitor | occupied tags mask | active tags mask | urgent tags mask |
|---------|--------------------|------------------|------------------|
| eDP-1   | 14                 | 6                | 0                |

## Virtual Monitors

You can create headless outputs for screen mirroring or remote desktop access (e.g., Sunshine/Moonlight).

```bash
# Create a virtual output
xctl -d create_virtual_output

# Configure it (set resolution)
wlr-randr --output HEADLESS-1 --pos 1920,0 --mode 1920x1080@60Hz

# Destroy all virtual outputs
mmsg -d destroy_all_virtual_output