# Git

## HEAD

- The HEAD is a pointer that represents the current commit in the current branch.
- It allows you to move between commits and branches.

## Remote

- A remote is a reference to a remote repository, typically hosted on a server like GitHub or GitLab.
- Common commands: `git remote add`, `git push`, `git pull`, `git fetch`.

## Merge

- Merging combines changes from one branch into another.
- `git merge` incorporates commits from another branch into the current branch.

## Rebase

- Rebasing applies commits from one branch onto the head of another branch.
- `git rebase` can be used to rewrite commit history, making it linear.

## Revert

- Reverting undoes changes introduced by a specific commit.
- `git revert` creates a new commit that inverts the changes from a previous commit.

## Squash

- Squashing combines multiple commits into a single commit.
- This is useful for cleaning up commit history before merging or rebasing.

## Cherry Pick

- Cherry-picking allows you to apply specific commits from one branch to another.
- `git cherry-pick` can be used to selectively incorporate commits.

## Pull Request

- A pull request is a way to propose and review code changes before merging them into a branch.
- Common in collaborative development workflows.

## Submodules

- Submodules allow you to include external repositories within your main repository.
- They are useful for managing dependencies or shared code.

## Reset

- The `git reset` command is used to undo local changes or remove commits from the current branch.
- It can be used with various options (`-soft`, `-mixed`, `-hard`) to control the scope of the reset.

## Amend

- Allows you to modify the most recent commit.
- It can rewrite history and potentially disrupt the workflow for others.
- `git commit --amend`

## Working Area vs Staging Area

- The working area is where you make local changes to files.
- The staging area (index) is where you stage changes before committing them.

## Bisect

- Git bisect is a tool for finding the commit that introduced a bug or regression.
- It performs a binary search through your commit history, helping you isolate the problematic commit.
