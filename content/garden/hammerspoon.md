---
title: Hammerspoon
date: '2024-10-01'
lastmod: '2026-07-07'
draft: false
keywords:
- Hammerspoon
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
---

[Hammerspoon](https://www.hammerspoon.org/) is a macOS automation bridge that exposes system APIs to Lua scripts through bundled extensions. We **adopt** it for keyboard-driven window management, menu bar utilities, and local glue that Shortcuts or AppleScript handle poorly.

## Blurb

> This is a tool for powerful automation of macOS. At its core, Hammerspoon is just a bridge between the operating system and a Lua scripting engine. What gives Hammerspoon its power is a set of extensions that expose specific pieces of system functionality, to the user.

## Summary

**When to use:**

| Use | Notes |
|-----|--------|
| **Window and app control** | Move, resize, focus, and tile windows with hotkeys |
| **Menu bar utilities** | Small scripts with `hs.menubar` for status and quick actions |
| **Local glue** | Wire CLI tools, notifications, USB events, and app launches together |
| **Personal macOS setup** | Version-controlled Lua in `~/.hammerspoon/` you reload on save |

**When to skip:**

- Cross-platform automation (Linux or Windows targets)
- Team-wide policies that need MDM-managed profiles
- Workflows Shortcuts or AppleScript already cover with less code

**Trade-offs:** Config is code, not clicks. Power users love it; shared machines need discipline so hotkeys do not surprise other users.

## Details

| Topic | Notes |
|-------|--------|
| **Entry point** | `~/.hammerspoon/init.lua`; reload with `hs.reload()` or the menu bar item |
| **Extensions** | `hs.window`, `hs.hotkey`, `hs.application`, `hs.menubar`, `hs.notify`, and many more in the docs |
| **Debug** | Built-in console and `hs.printf()` for printf-style tracing |
| **Distribution** | No app bundle to ship; each user maintains their own config folder |
| **Example config** | Public reference: [jkamenik/.hammerspoon](https://github.com/jkamenik/.hammerspoon) |

**References**

- [Hammerspoon documentation](https://www.hammerspoon.org/docs/)
- [Getting Started](https://www.hammerspoon.org/go/)
