# Git and GitHub for Beginners - Crash Course

This course by Gwendolyn Faraday of [Faraday Academy](https://www.youtube.com/c/FaradayAcademy/) is available on [FreeCodeCamp](https://www.freecodecamp.org/news/git-and-github-crash-course/). These are notes to save myself from having to Google the same things over and over again.

Here we go.

## Terms
| Term | Actual Meaning |
| --- | --- |
| Directory | Folder |
| Terminal/Command-line | Interface for Text Commands |
| CLI | Command-line Interface |
| cd | Change Directory |
| Code Editor | Word Processor for Coding |
| Repository (repo) | Project or folder/place where your project is kept |
| GitHub | A website to host your repositories online |

## Git Commands
| Command | What it does |
| --- | --- |
| `git clone <link of repository>` | Bring a repository hosted remotely (like GitHub) into a local folder |
| `git add .(for all or) <file name>` | Track files and changes in Git |
| `git commit -m "<title>" -m "<description>"` | Save files in Git. Description is optional (title is required) |
| `git push` | Upload Git commits to a remote repo (liek GitHub) |
| `git pull` | Download changes from remote repo to local folder (ie opposite of `git push`) |
| `git status` | Returns up-to-date Git status for files in current directory |
| `git remote -v` | Returns the origin required for push |
| `git branch` | Returns branch structure in current repo |
| `git checkout <name of branch>` | Switch between branches. Add `-b <name of new branch>` to create new branch and switch to it |
| `git merge main` | Called in branch to updates file in branch with the same in main |
| `git merge <name of branch to be merged>` | Called in main to merge branch back into main |
| `git log` | Returns a list of commits with unique hash numbers; type `q` to escape |

## Signup to GitHub, Create a repo and README
- pretty intuitive

## Check Git Version on Local Computer
- open a Terminal, type `git --version`
- install if necessary by typing `brew install openssl` (in a Mac Terminal)

## Use a Code Editor (optional but highly recommended)
- I'm using IDLE and Visual Studio Code (VS Code) for Python3

## Set Up SSH Key
- must be set up before `git push`
- instructions [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- demonstration by Gwen in the [video](https://youtu.be/RGOj5yH7evk?t=1231) (20:31-25:23)
- **do not share your private key**

## To Pull repo Made Remotely
- type `git clone <link of repo (HTTPS or SSH)>` in Terminal 
- cd into new local foler (`pwd` to check) and type `ls -la` to see if .git folder is there

## To Push Updated Local Directory
- if local directory already has a .git foler (ie created and pulled from remote): 
    1. type `git add .(for all or) <file name>` in Terminal (make sure you're in the correct directory) to track files/changes
    2. type `git commit -m "<title>"` to save files/changes. After first commit, `git commit -am "<title>"` will combine steps 1-2
    3. type `git push -u origin main` to upload files/changes for the first time (`git push` thereafter) 

- <mark>feel free to use `git status` along the way to track progress</mark>
- if local directory is created locally (ie not yet known remotely):
    1. check if you're in the right directory by using `pwd`
    2. turn it into a Git repo by typing `git init` (results in the creation of a .git folder)
    3. `git add .(for all or) <file name>`
    4. `git commit -m "<title>"`. After first commit, `git commit -am "<title>"` will combine steps 3-4
    5. create an empty repo on GitHub and copy its HTTPS or SSH link
    6. come back to Terminal and type `git remote add origin <link of repo (HTTPS or SSH)>` (`git remote -v` to check if origin set up correctly)
    7. `git push -u origin main` to upload files/changes for the first time (`git push` thereafter) 

## Branching
- see current structure by typing `git branch`
- swithch into an existing branch with `git checkout <name of branch>` or create a new one with `git checkout -b <name of new branch>`
- first add, commit, and push as usual
- to merge branches:
    1. `git diff <name of branch>` to see differences between same file in different branches; hit `q` to escape
    2. `git checkout <name of branch>` to get into the branch
    3. `git commit -am "title"` to save changes if needed (assuming it's not a first add/commit)
    4. `git push -u origin <name of branch>` to upload
    5. create a pull request on GitHub (easy way)
        - pay attention to the arrow
        - make sure description of changes is clear/concise
        - add comments at the line of code and Resolve conversation if needed
        - click Merge Pull Request
    6. in main `git pull -u origin main` (first time; `git pull` thereafter) to update local files
    7. do not reuse branch, so delete it using `git branch -d <name of branch to be deleted>`
- dealing with conflicts:
    1. `git diff <name of branch>` to see differences between same file in different branches; hit `q` to escape
    2. `git checkout <name of branch>` to get into the branch
    3. `git merge main` to keep file in branch updated
    4. conflict will be highlighted in VS Code; resolve and `git commit -am "title"` to save resolution
    5. your local branch file should now be reconciled to the same remote file in main

## Undo
- undo `git add` with `git reset` (name of file can be added to undo staging of specific file)
- undo `git commit` with `git reset HEAD~1`
- undo any commit in `git log` with `git reset <unique hash number>` (adding `--hard` in front of the hash number deletes all changes from that commit)

## Fork
- click Fork on other people's GitHub repo to make a copy of it to your own GitHub account
- this gives you complete control of the code to develop as you will (muhahaha...?)
- a dev branch will be created by default

---
Patrick Lee MacLeod 🦄