# github-notes

Git is a software that allows you to keep track of changes made to a project over time. Git works by recording the changes you make to a project, storing those changes, then allowing you to reference them as needed.

## Git Workflow
1)	A Working Directory: where you'll be doing all the work: creating, editing, deleting and organizing files
2)	A Staging Area: where you'll list changes you make to the working directory
3)	A Repository: where Git permanently stores those changes as different versions of the project
    a.	Changes are saved as a commit

`git init`

* Initializes an empty Git repository in the current working directory.
*	Sets up the tools Git needs to begin tracking changes on the current project.
*	Creates a hidden folder /.git/ in the directory where git operates.

`git status`
*	Lists any changes of the contents in the working directory.
*	Untracked files will be displayed in red
    *	Untracked files do not have any changes stored.
*	Green files show changes to a file that need to be committed.

`git add <file>`
*	Adds the specified file to be committed (commit) to the repository and tracks changes on the file

`git remote add <remote name> <URL>`
`git remote add origin https://github.com/user/repo.git`
*	<URL> is the destination of a remote repository.
*	The name is anything you give it.
*	This adds your local repo to the remote one.


`git diff <file>`
*	Displays changes to a tracked file between the local file and those added to the staging area
*	Additions to the file are preceded by a + and in green
*	Any missing lines are preceded by a – and in red
*	The same lines are in white

`git diff HEAD`
*	The most recent change to the last file you committed.
 
## Branches
`git branch`
*	Lists all branches of repository
*	Current branch is preceded by an asterisk

`git status`
*	Lists the current branch and any differences
*	When it says 'up-to-date' it means up-to-date with the branch that the current branch tracks.
    * Usually this is the local reference
    * Not "up-to-date with the latest live status of the upstream.

`git checkout -b <branch-name>`
*	Create a new branch locally.

`git push -u <origin> <branch-name>`
*	To push a local new branch to the remote
*	-u stands for –set-upstream
    * tells git to remember all of the commands so that <git push> will execute the same command as an alias now.

`git pull <origin> <branchName>`
*	Returns any changes that have been made to the files under the folder name.

`git commit`
*	Any files added to the unstaged area which have been changed can be committed to the repository.

`git fetch`
*	A local repo won't reflect changes that have been made on the remote repo, so it must be updated first before changes are made.
*	fetch gets up to date with the commits from the remote repo

`get merge`
*	merge moves those commits to the local branch

`git pull`

### Check Differences Between Branches
`git fetch`
*	Run git fetch first to make sure the local branch is updated.

`git branch`
*	List all available branches

`git diff (local-branch) (remote-branch)`
*	Compare the differences between each branch.
*	The first listed branch is considered branch A and the second branch is branch B
*	Any changes that are within A that are not in B are preceded by a – and listed in red.
*	Any changes within B but not in A are preceded with a + and listed in green.

## Using Git with Github
1.	Initialize the local directory as a git directory
`git init`
2.	Add all files currently in the directory to be staged for commit
`git add .`
3.	Commit the files you've staged
`git commit -m "First commit"`
4.	Create the new repository on github
5.	Get the github repository's URL from the quick setup page
6.	Add the url for the remote repository
`git remote add origin <URL>`
`git remote -v`
7.	Push the changes to master branch
`git push origin master`

## Git URLs
*	Git provides https or SSH to download and upload.
### SSH
* Github email address is address you use to login
`ssh-keygen -t rsa -b 4096 -C “email@address.com”`
*	An SSH key will be generated in a file.
*	Must input a passphrase for the SSH key
*	ssh-agent manages your SSH keys.
    * the key must be added to ssh-agent to use
*	Generate an agent id:
`eval $(ssh-agent -s)`
*	Add the private key to the ssh-agent
`ssh-add ~/.ssh/id_rsa`
### Add SSH to GitHub Account
*	Check for existing keys
`ls -al ~/.ssh`
    * will have a .pub extension for the public key
    * The private key will be the same name without the .pub extension

*	Copy the SSH key to your clipboard
`clip < ~/.ssh/id_rsa.pub`
*	Go to your Settings at github.
*	Click on SSH and GPG keys
*	The “Title” field is only descriptive.
    * Name it after the computer that is accessing github
*	“Key” field
    * The SSH key that was generated through ssh-keygen
 
## Common Errors
```bash
git push -u <origin> <branch>
ssh: Could not resolve hostname https: Name or service not known.
```
*	The hostname stored in origin is most likely wrong.
*	Double check it with:
`git remote -v`
*	To change the url:
`git remote set-url <origin> <URL>`

```bash
git push -u <origin> <branch>
remote: Repository not found
```

```
git checkout
you are on a branch yet to be born
```
*	Make sure the repository has been initialized locally
*	Make sure the repository exists on github.
*	Make sure the local repository knows of the remote repository.
    * Double check it with: `git remote -v`
        * If it does not know of the remote repository, get the repository’s address from github.

`git remote add <origin-name> <url>`
*	Add the contents of the folder to be staged: `git add .`
*	Commit the file: `git commit -m “commit message”`
*	Double check you are on the same branch you are trying to push to `git status`
*	If you are not, check the local branches: `git branch`
*	If it does not exist locally `git checkout -b <branch-name>`
*	Push the file `git push -u <origin-name> <branch-name>`
