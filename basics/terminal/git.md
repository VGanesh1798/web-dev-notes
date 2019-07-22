# Git Commands
Git is a version control system with a really cool branching feature. It can be downloaded on all platforms and is often used in conjunction with a remote repository like GitHub, GitLab, or BitBucket.

## Initial Git Setup
There are three stages of the Git config, and each stage overrides the last.
- The system level config, with flag `--system`, is in /etc/ and requires superuser permissions to modify.
- The user's config, with flag `--global`, is in their home folder.
- The local config, with flag `--local`, is in the .git folder of a repository. This is also the default stage when making changes to a git config file.

It's typically a good idea to set the global config:

`git config --global user.name NAME` to set your name, in quotes.

`git config --global user.email EMAIL` to set your email.

`git config --global core.editor EDITOR` to set your text editor.

To view your settings, run `git config --list`.

## Getting Help
You can either read the man page for Git or run one of the following commands to get help for a specific git command:
- `git help COMMAND`
- `git COMMAND --help`
- `git COMMAND -h`
- `man git-COMMAND`

## Ignoring Files
In a .gitignore file, you can define all of the files and folders you don't want to be tracked for changes. For example, a node_modules folder takes up a lot of space and is useless to push into a repository, and a credentials.json file might have sensitive information. You can ignore these to prevent git from tracking them.

## Basic Git Commands
```
git init                # Initialize a directory as a git repo
git clone URL           # Clone remote repository from URL, by HTTPS or SSH

git status              # Shows modified files and staging status
git diff                # Outputs uncommitted changes
git log                 # View commit history

git add FILE            # Stage modified FILE
git add -A              # Stage all modified files
git rm FILE             # Removes FILE from being tracked
git mv FILE NEW_FILE    # Renames FILE to NEW_FILE for git

git commit              # Commit staged files
git commit -a           # Commit all files, skipping staging
git commit -m MESSAGE   # Commit and type message, in quotes, on command line
git commit --amend      # Make changes to last commit

git reset HEAD FILE     # Unstage FILE
git checkout -- FILE    # Discard changes to FILE

git tag                 # Show all tags
git tag -a TAG          # Add a new TAG
git show TAG            # Show information for TAG
```

## Remote Repository Commands
```
git remote                            # List remote branches
git remote add REMOTE URL             # Add a new REMOTE branch for URL
git remote show REMOTE                # Show information about REMOTE
git remote rename REMOTE NEW_REMOTE   # Rename REMOTE to NEW_REMOTE
git remote remove REMOTE              # Remove REMOTE branch

git fetch REMOTE                      # Fetch changes made to REMOTE
git pull                              # Pull remote changes (fetch and merge)
git push                              # Push changes to remote branch
git push REMOTE BRANCH                # Push BRANCH changes to REMOTE
```

## Branch Commands
```
git branch BRANCH                 # Create BRANCH
git branch -v                     # View most recents commits in all branches
git checkout BRANCH               # Switch HEAD to BRANCH

git checkout -b BRANCH            # Create BRANCH and switch HEAD to BRANCH
git checkout -d BRANCH            # Delete BRANCH; won't work if unmerged
git checkout -D BRANCH            # Forcibly delete BRANCH

git merge BRANCH                  # Merge BRANCH changes into current branch

git push REMOTE BRANCH            # Push BRANCH to REMOTE
git push REMOTE --delete BRANCH   # Delete BRANCH from REMOTE

git rebase BRANCH                 # Rewind commit history of BRANCH

git stash                         # Stash changes for later
git clean                         # Get rid of unstaged changes
```
