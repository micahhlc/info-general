# Ensure you are on the main branch
git checkout main

# Fetch the latest changes from remote without merging
git fetch origin

# Pull the latest changes from the remote main branch
git pull origin main

# View commit history in a clean format
git log --oneline --graph --all

# View changes before committing
git status

# Add all changes to staging
git add .

# Add a specific file to staging
git add <file-name>

# Commit changes with a message
git commit -m "Your commit message"

# Amend the last commit (only if not pushed yet)
git commit --amend -m "Updated commit message"

# Push the latest changes to remote main branch
git push origin main

# Force push if necessary (use with caution)
git push --force origin main

# Unstage a file (keep changes)
git reset <file-name>

# Unstage all files (keep changes)
git reset

# Undo last commit but keep changes
git reset --soft HEAD~1

# Undo last commit and discard changes
git reset --hard HEAD~1

# reset and retrieve from origin/main overwriting local
git reset --hard origin/main

# Discard changes in a specific file
git checkout -- <file-name>

# Remove untracked files (use with caution)
git clean -fd

# Show the last commit details
git show HEAD

# Show what changed in the last commit
git diff HEAD^

# View remote repository details
git remote -v
