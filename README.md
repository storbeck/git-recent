# git-recent

Quickly switch between your recently used Git branches with an interactive menu.

## Quick Start

```bash
# Download and install (zsh default)
curl -O https://raw.githubusercontent.com/storbeck/git-recent/main/git-recent
chmod +x git-recent && mv git-recent /usr/local/bin/

# Set up git alias (optional but recommended)
git config --global alias.recent "!git-recent"

# Use it
git recent
```

## What it does

Shows a numbered list of your recently checked-out branches and lets you switch to any of them by entering the number.

```
Recently used branches:
----------------------
1) feature/user-auth
2) develop  
3) main *
4) hotfix/critical-bug

Enter number to switch to that branch (or press Enter to cancel):
```

**Requirements:** Git and zsh (default macOS shell)

## Usage

```bash
git recent     # Show 10 recent branches
git recent 5   # Show 5 recent branches
```

Type a number and press Enter to switch, or just press Enter to cancel.

## Using fish shell

The original fish implementation ships as `git-recent.fish`. If you prefer to use that version:

```bash
curl -O https://raw.githubusercontent.com/storbeck/git-recent/main/git-recent.fish
chmod +x git-recent.fish && mv git-recent.fish /usr/local/bin/git-recent.fish
funcsave git-recent.fish  # optional: make it available as a fish function
```

Then update your fish config or alias to call `/usr/local/bin/git-recent.fish` (or source it as a function) when running `git recent`.
