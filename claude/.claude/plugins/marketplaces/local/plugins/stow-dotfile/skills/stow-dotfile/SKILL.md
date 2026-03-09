---
name: stow-dotfile
description: This skill should be used when the user wants to "stow" a file, "version control a config", "move a config to dotfiles", "add a dotfile", or manage configuration files with GNU Stow. Handles moving config files to ~/dotfiles and symlinking them back using stow.
version: 1.0.0
---

# Stow Dotfile Manager

You are an expert in GNU Stow. When the user wants to manage a configuration file (e.g., `~/.config/ghostty/config`), follow this strict procedure to avoid data loss.

## Prerequisites
1. Verify `stow` is installed (`which stow`).
2. Verify `~/dotfiles` exists.
3. Verify the target file exists in the home directory.

## The Algorithm
To stow a file located at `~/$REL_PATH`:

1. **Determine Package Name**:
   - If the user provides a package name (e.g., "ghostty"), use it.
   - If not, derive it from the path (e.g., `~/.config/nvim/...` -> `nvim`).

2. **Calculate Destination**:
   - The physical file must move to: `~/dotfiles/$PACKAGE_NAME/$REL_PATH`.
   - *Crucial*: You must replicate the full folder structure inside the package directory.
   - Example: `~/.config/ghostty/config` -> `~/dotfiles/ghostty/.config/ghostty/config`.

3. **Execution Steps** (Run these using the `bash` tool):
   a. Create the parent directory:
      `mkdir -p ~/dotfiles/$PACKAGE_NAME/$(dirname $REL_PATH)`
   b. Move the file:
      `mv ~/$REL_PATH ~/dotfiles/$PACKAGE_NAME/$REL_PATH`
   c. Stow the package:
      `cd ~/dotfiles && stow $PACKAGE_NAME`

## Safety Rules
- **NEVER** run `stow` if the target file still exists in Home (it causes conflicts). Move the file *first*.
- **ALWAYS** check for `stow` conflicts (e.g., existing symlinks) before proceeding.
- If the file is already a symlink pointing to `~/dotfiles`, do nothing and inform the user.

## Example
User: "Stow my .bashrc"
Action:
1. `mkdir -p ~/dotfiles/bash`
2. `mv ~/.bashrc ~/dotfiles/bash/.bashrc`
3. `cd ~/dotfiles && stow bash`
