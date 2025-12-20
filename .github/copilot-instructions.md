# Hyprland Dotfiles (JaKooLit) AI Instructions

This repository contains configuration files for the Hyprland window manager, based on JaKooLit's dotfiles. It uses a specific structure to separate default configurations from user customizations.

## 🏗 Architecture & Structure

The configuration is modular, with `hyprland.conf` acting as the entry point that sources other files.

- **`hyprland.conf`**: The main configuration file. It sources files from `configs/` and `UserConfigs/`.
- **`configs/`**: Contains **DEFAULT** configurations (e.g., `Keybinds.conf`).
    - ⚠️ **DO NOT EDIT** files in this directory directly. They may be overwritten during updates.
- **`UserConfigs/`**: Contains **USER** configurations.
    - ✅ **EDIT THESE FILES** for customizations.
    - `Startup_Apps.conf`: Applications to run on launch (`exec-once`).
    - `UserKeybinds.conf`: Custom keybindings.
    - `WindowRules.conf`: Window and layer rules.
    - `UserSettings.conf`: General settings (input, gestures, misc).
    - `UserDecorations.conf`: Visual settings (borders, rounding).
    - `UserAnimations.conf`: Animation settings.
    - `ENVariables.conf`: Environment variables.
- **`scripts/`**: Core system scripts (updates, utilities, menus).
- **`UserScripts/`**: Custom user scripts.

## 🚀 Workflows & Best Practices

### Configuration Changes
1.  **Identify the Scope**: Determine if the change is a core setting or a user preference.
2.  **Edit the Correct File**:
    - For keybinds: Check `configs/Keybinds.conf` for conflicts, then add to `UserConfigs/UserKeybinds.conf`.
    - For autostart: Add to `UserConfigs/Startup_Apps.conf`.
    - For visual changes: Edit `UserConfigs/UserDecorations.conf` or `UserConfigs/UserAnimations.conf`.
3.  **Reload**: Changes usually require reloading Hyprland (`hyprctl reload`) or restarting the session.

### Scripting
- **Language**: Bash (`#!/bin/bash`).
- **Notifications**: Use `notify-send` for user feedback.
- **Dependencies**: Check for required tools (e.g., `kitty`, `rofi`, `swaync`) before execution.
- **Paths**: Use absolute paths or variables (e.g., `$HOME/.config/hypr/...`) to ensure reliability.

## ⚠️ Conventions & Gotchas

- **File Renaming**: Do **NOT** rename files in `UserConfigs/` as they are hardcoded in `hyprland.conf`.
- **Updates**: The `UserConfigs/` and `UserScripts/` directories are designed to persist across updates. Modifications outside these folders may be lost.
- **Syntax**: Follow standard [Hyprland Wiki](https://wiki.hyprland.org/) syntax.
    - Example: `bind = MOD, KEY, dispatcher, params`
    - Example: `windowrulev2 = rule, title:^(regex)$`

## 🔍 Key Files Reference

- `hyprland.conf`: Main loader.
- `configs/Keybinds.conf`: Default keymap (Reference only).
- `UserConfigs/Startup_Apps.conf`: `exec-once` definitions.
- `UserConfigs/WindowRules.conf`: `windowrule` and `windowrulev2` definitions.
- `scripts/`: Utility scripts for system management.
