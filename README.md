# gitted
A short, sweet, easy tutorial on Git
Originally created by Bokai Bi (Discord @KoishiHat)

Git manages the versioning of files inside a folder (called a Git repository). Versions are stored in "commit"s. Each version is called a commit. A commit contains a snapshot of all the files at the point of committing. 

# Cheat Sheet
## Common commands
`git clone [link]` - Downloads a repository from the link.  
`git status` - Shows changes made since the last commit.  
`git add [filename]` - Adds an uncommitted change to be included in the next commit.  
`git commit -m [message]` - Creates a commit with all the `add`ed changes. [message] should describe what was changed in this commit.  
`git push` - Pushes all local commits to the cloud (remote).  
`git pull` - Pull changes from the cloud (remote) to the current local branch.  

## Occasionally useful commands
`git log` - Shows a history of commits with their commit ids.
`git reset --hard [commit-id]` - ***DANGEROUS*** Resets the local branch to the specified commit. Make sure to back up changes you want to keep somewher eoutside the repo. 
`git reset --hard origin/main` - Same as above, but resets the local branch to the current remote main branch

