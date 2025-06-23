# git-recent

A simple Fish shell script to show and interactively switch between recently used Git branches.

## What it does

`git-recent` shows you a numbered list of your most recently checked-out Git branches and lets you quickly switch to any of them by entering the corresponding number.

## Features

- Shows up to 10 recent branches by default (configurable)
- Highlights your current branch with an asterisk (*)
- Interactive branch switching with number selection
- Filters out duplicate branches and HEAD references
- Simple, fast, and lightweight

## Requirements

- [Fish shell](https://fishshell.com/)
- Git

## Installation

1. Download the `git-recent` script
2. Make it executable: `chmod +x git-recent`
3. Move it to a directory in your PATH, such as:
   ```bash
   mv git-recent /usr/local/bin/
   ```
   Or add it to your Fish functions directory:
   ```bash
   cp git-recent ~/.config/fish/functions/
   ```

## Usage

Show the 10 most recent branches:
```bash
git-recent
```

Show a custom number of recent branches:
```bash
git-recent 5    # Show 5 recent branches
git-recent 20   # Show 20 recent branches
```

### Example output

```
Recently used branches:
----------------------
1) feature/user-auth
2) develop
3) main *
4) hotfix/critical-bug
5) feature/new-dashboard

Enter number to switch to that branch (or press Enter to cancel):
```

Type a number (e.g., `1`) and press Enter to switch to that branch, or just press Enter to cancel.

## How it works

The script uses `git reflog` to find recent branch checkouts, parses the output to extract unique branch names, and presents them in a numbered list. When you select a number, it runs `git checkout` to switch to that branch.

## License

MIT License - feel free to use, modify, and distribute as you see fit.

## Contributing

Issues and pull requests welcome! This is a simple utility script, but improvements and bug fixes are always appreciated.