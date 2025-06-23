#!/usr/bin/env fish

# Git-recent: A script to show and switch between recently used git branches
# Number of recent branches to show (default: 10)
set count $argv[1]
if test -z "$count"
    set count 10
end

# Get the current branch
set current_branch (git symbolic-ref --short HEAD 2>/dev/null)

# Get a list of recently checked-out branches
set recent_branches (git reflog --no-abbrev | \
                    grep -i 'checkout: moving from' | \
                    awk '{print $6, $8}' | \
                    grep -v '^$')

# Display the branches with numbers
echo "Recently used branches:"
echo "----------------------"

# Create an array to store branch names
set -l branches

# Process the reflog output
for line in $recent_branches
    # Extract the branch name (it's in pairs, so we need every other entry)
    set -l parts (string split " " $line)
    set -l from_branch $parts[1]
    
    # Skip if branch is empty or HEAD
    if test -n "$from_branch" -a "$from_branch" != "HEAD"
        # Check if branch is already in our list
        if not contains $from_branch $branches
            set -a branches $from_branch
        end
    end

    if test (count $branches) -ge $count
        break
    end
end

# Print the unique branches with numbers
set i 1
for branch in $branches
    # Mark the current branch with an asterisk
    if test "$branch" = "$current_branch"
        echo "$i) $branch *"
    else
        echo "$i) $branch"
    end
    set i (math $i + 1)
end

# Ask to switch if we found branches
if test (count $branches) -gt 0
    echo ""
    echo "Enter number to switch to that branch (or press Enter to cancel):"
    read -l choice
    
    # Switch to the selected branch if a valid number was entered
    if string match -rq '^[0-9]+$' "$choice"
        if test $choice -ge 1 -a $choice -le (count $branches)
            set selected_branch $branches[(math $choice)]
            echo "Switching to branch: $selected_branch"
            git checkout "$selected_branch"
        end
    end
else
    echo "No recent branches found."
end
