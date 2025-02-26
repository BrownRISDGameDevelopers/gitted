# gitted
A short, sweet, easy tutorial on Git for BRGD  
Originally created by Bokai Bi (Discord @KoishiHat)

Git is used to manage the versions of files inside a folder (called a Git repository). Each version is called a commit. A commit contains a snapshot of all the files at the point of committing. 

# Cheat Sheet
## Common commands
`git clone [remote link]` - Downloads a repository from the remote link.  
`git status` - Shows changes made since the last commit.  
`git add [filename]` - Adds an uncommitted changed file to be included in the next commit.  

- You can add all files in current folder with `git add *`
 
`git commit -m [message]` - Creates a commit with all the `add`ed changes. [message] should describe what was changed in this commit.  
`git pull` - Pull changes from the cloud (remote) to the current local branch.  
`git push` - Pushes all local commits to the cloud (remote). You always want to pull before you push.  

## Occasionally useful commands
`git log` - Shows a history of commits with their commit ids.  
`git reset --hard [commit-id]` - ***DANGEROUS*** Resets the local branch to the specified commit. Make sure to back up changes you want to keep somewher eoutside the repo.  
`git reset --hard origin/main` - Same as above, but resets the local branch to the current remote main branch.  

## Fundamentals of Merge Conflict Resolution
You typed `git pull` and was told you have a merge conflict. Don't worry because it's not that bad!  
Merge conflicts happen because someone pushed changes to the remote that conflict with your local committed changes. You need to manually tell Git how to resolve the conflict.  
Here are some common steps:
`git status` - See which files currently contain unresolved merge conflicts  
If the file is not in a human-readable text format (like an image or video), you should delete the file and re-add the correct version. If it's semi-human readable (like a Unity scene), find an expert or proceed with caution if you want to merge manually.  
Otherwise, you can open the file in your favorite text editor. You should see 1 or more sections that look like this:  
```
My favorite Touhou song is  <- Normal, nonconflicting content 
<<<<<<< HEAD                
Hartmann's Youkai Girl      <- your local changes are here
=======
Bad Apple                   <- remote changes are here
>>>>>>> [commit id of the remote]
```
This lays out what content are actively in conflict. Decide what you want to final file to look like, then delete everything else (including the merge conflict markers).  
Make sure to scan the rest of the file to make sure your final file makes sense! If the remote commit include changes A and B, where A depends on B, it could happen that only B conflicts with your local changes. If you decide to remote B, you should take A into consideration too.  
```
My favorite Touhou songs are Hartmann's Youkai Girl and Bad Apple.
```
Now save your file and go back to the terminal:  
`git add [file in conflict]` - Add the new merge conflict resolution changes to the next commit
`git commit -m [message]` - Commit your resolution
`git push` - Push your changes. Note if someone pushed more changes while you were resolving the conflict you'll need to `git pull` first. If that creates another conflict, you can resolve it in the same way.  

## Common issues
- I got something like this: ![6ijwK](https://github.com/user-attachments/assets/57c5b6ad-43d1-4d83-bb32-a6b7c36c8f36)
  - Type: `git config --global pull.rebase false`. Git is asking you how to deal with divergent branches. Merge is the strategy we want to use.
- I messed around with branches and got a DETACHED HEAD
  - This is a rather complicated problem so we won't cover it here. Imo we should avoid using branches at BRGD since our scale is small enough.
- I'm having trouble authenticating to GitHub
  - The VSCode terminal is authenticated automatically with GitHub if you're logged in and this is a cheap solution. For more permanent authentication, check online!
