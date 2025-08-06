#versioncontrol

A version control tool can help maintain large complicated projects. Git is a command-line tool that we can use to 1) keep track of changes to software, 2) allow multiple people to work on a single application or piece of software and to sync the work, or 3) make changes to code without removing access to the original by branching and then merging into the main branch, and 4) we can revert back to older versions of code. 

Code is stored in a remote repository with changes uploaded from local changes (usually, changes can be made remote via certain interfaces). The changes can be pulled down by other local users. Conflicts between code can occur and be dealt with in simple ways. 

Git has many hosting platforms, but the big ones are GitHub, GitLab, and Bitbucket. 

# Repositories

A repo is nothing more than a remote file structure with fancy management tools. When a repo is downloaded (or cloned) locally, it's put into a folder that is the title of the repository, and then all content is simply navigable files. 

By using a public hosting service, anyone in the world with internet can access the code that a user has written. 
### Cloning a Repository

Repo's are cloned with SSH or HTTP with

`git clone <SSH or HTTP link>`

Where the link is available from a git hosting website. For SSH, you need to add SSH keys locally. 

# Make Changes

When in a repository, treat it like any other folder and make changes as necessary.

### Updating the Remote Repository

There are a series of commands needed to `push` changes to the remote repository. 
#### Add

Add allows us to add a file to Git as a file to track, done with the simple

`git add <file or folder>`

This way, you can make local changes but only the files you deliberately want to be tracked will be tracked. You probably don't want to save all the junk files for every commit, or files that are still being worked. 
#### Commit

Saves a snapshot of the state of all the files and folders and assets in a repository to refer back to them in the future. 

`git commit -m "sample message"`

It's important to include a concise but descriptive commit message to describe the commit for future reference, especially on large projects with lots of commits. It's only easy or valuable to refer to a commit with a good description. 

There's  a shortcut for adding and committing at the same time:

`git commit -am "sample message"`

Note that this adds and commits all of the files that have been changed, not necessarily desirable behavior all of the time. 
#### Push

Publish your changes and commits up to the server with the command

`git push`

So that the remote (online version of the) repository has access to all the changes that a user has made. Now the changes can be seen online. 

#### Pull

When changes are made by remote entities, one can update the local status of their repo to be the latest version online by issuing

`git pull`

Which will grab the changes and merge them with the local codebase. 

# Conflicts

When making changes with other people, conflicts between changes are inevitable. When one user tries to change a file that's also been changed, they may be faced with a **merge conflict**. Git is pretty smart so this isn't always the case but it's not uncommon. 

This is most commonly faced when pulling in remote changes from the repository after committing similar changes and you will be faced with a conflict message from git, something like.

```
CONFLICT (content): Merge conflict in foo.py
Automatic merge failed, fix conflicts and then commit results. 
```
Git then automatically adds metadata to the file to describe the conflict like this

```
...
<<<<< HEAD
local changes
=====
remote changes
>>>>> 54b15...conflicting commit hash...748c92
...
more code
...
```

Addressing a conflict is as simple as removing all of the conflict code, fixing it, and committing and pushing.

# Branches

A simple linear structure to development can make things messy. So git provides a method to work on changes without disturbing another codebase (usually main). This is achieved by **branches**, which allow a user to branch off of one repo with essentially a save state of it and work on different parts of the repo such as new features or bug fixes in isolation, simultaneously. 

`HEAD` is the current working version or state of a branch. It can be changed to point to a given branch or main or whatever. Switching the `HEAD` is how you switch branches. 

Here are some useful branching tools

#### Git branch

Running `git branch` will tell you what branch you're currently on and what other ones you recently have been on. `git branch -a` will tell you all branches.

#### Switch between branches

A user can quickly switch between branches (assuming all changes have been committed to each respective branch) with the checkout command.

`git checkout <branch-name>`

#### Create a new branch

**Note**: In a professional setting, branches are almost always created through the git hosting website's interface. 

Creating a new branch is done by adding some branch options to the regular branching command: `git checkout -b <new-branch-name>`

Which will create a new branch and will put you on it. 

#### Merging Changes

A basic way to merge changes on one branch to another is to first checkout the branch you want the changes to be merged into, then issue the following command. 

`git merge <branch-name>`

Occasionally this will cause a merge conflict as well, which should be resolved the usual way on the branch that was attempted to be **merged into**. So usually, one should merge main into the working branch. 

# Forking

A user can make a copy of a repository, make changes, and merge them into the main repository with a pull request. 

# Github Pages

Github allows any user to create and publish a **static** website. Traditionally this would be done by creating a new repository with the name being `username.github.io`. This will automatically be supporting github pages.

Add an `index.html` to the repository and commit and push it up to GitHub. In settings, GitHub pages with the repo just made will be ready to be published, and the website will be ready. 

This is an easy way to maintain a website since GitHub will basically maintain all of the infrastructure. 

# Other useful Git tools

#### Git status

This command tells a user the current state of their local repository. By issuing the following command

`git status`

Git will tell you the difference between the local version and the origin version (usually up on a remote server)

#### Git log

`git log` can describe all of the commits that have happened over the course of some amount of time. It's a quick history of the repository. 

#### Reset

A user can take one state of the repository and revert it back to an older state via some of the following ways

`git reset --hard <commit>` will reset back to a commit with a given hash
`git reset --hard origin/main` will reset back to the remote repository version

