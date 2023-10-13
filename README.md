# GIT Commands

## Delete File from Git Repo

If you want to remove the file from the Git repository and the filesystem, use:

```
git rm file1.txt
git commit -m "remove file1.txt"

```
But if you want to remove the file only from the Git repository and not remove it from the filesystem, use:

```
git rm --cached file1.txt
git commit -m "remove file1.txt"
```

## Remove Git Repo

```
rm -rf .git
```

## Adding to Git Repo

```git add -A``` stages all changes
```git add .``` stages new files and modifications, without deletions (on the current directory and its subdirectories).
```git add -u``` stages modifications and deletions, without new files


## Set Default Branch

```
 git config --global init.defaultBranch main
```

## Clone a Repo

You clone a repository with ```git clone <url>```. For example, if you want to clone the Git linkable library called ```libgit2```, you can do so like this:

```
$ git clone https://github.com/libgit2/libgit2
```
--------------------------------------------------------------------------------------------

If you want to clone the repository into a directory named something other than ```libgit2```, you can specify the new directory name as an additional argument:

```
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

## Checking Your Settings

If you want to check your configuration settings, you can use the ```git config --list``` command to list all the settings.
To exit the settings Press ```q``` .

## Vim mode

To insert in the vim mode: Press ```Insert Key```
To exit the vim mode: Press ```Esc Key``` and then ```:x``` or ```:wq```

## View changes in Detail:

If the ```git status``` command is too vague for you — you want to know exactly what you changed, not just which files were changed — you can use the ```git diff``` command.

![](images/view%20changes.png)

--------------------------------------------------------------------------------------------
If you want to see what you’ve staged that will go into your next commit, you can use ```git diff --staged```.
--------------------------------------------------------------------------------------------
It’s important to note that ```git diff``` by itself doesn’t show all changes made since your last commit — only changes that are still unstaged. If you’ve staged all of your changes, ```git diff``` will give you no output.

## Rename File:

If you want to rename a file in Git, you can run something like: ```git mv README.md README```

## Viewing the Commit History

When you run ```git log``` in project, you should get output that looks something like this:
```
$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    Remove unnecessary test

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    Initial commit
```
--------------------------------------------------------------------------------------------
One of the more helpful options is ```-p``` or ```--patch```, which shows the difference (the patch output) introduced in each commit. You can also limit the number of log entries displayed, such as using ```-2``` to show only the last two entries.

![](images/commit%20history.png)
--------------------------------------------------------------------------------------------
Another really useful option is ```--pretty```. This option changes the log output to formats other than the default. A few prebuilt option values are available for you to use. The ```oneline``` value for this option prints each commit on a single line, which is useful if you’re looking at a lot of commits.

![](images/commit%20history%202.png)

## REDO Commit

If you want to redo that commit, make the additional changes you forgot, stage them, and commit again using the ```--amend``` option:
```git commit --amend``` 

## Delete a commit

```
git reset --hard HEAD~1
``` 

## Unstaging a Staged File

let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type ```git add *``` and stage them both. How can you unstage one of the two?
```
git reset HEAD houses.txt 
```

## Unstaging a Staged File with git restore

let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type ```git add *``` and stage them both. How can you unstage one of the two?
```
git restore --staged houses.txt
```

## Unmodifying a Modified File with git restore

What if you realize that you don’t want to keep your changes to the CONTRIBUTING.md file? How can you easily unmodify it — revert it back to what it looked like when you last committed
```
git restore houses.txt
```

## See the current remote origin

if you want to see the current remote origin to which you are commiting to, use: ```git remote -v```.

![](images/current%20remote%20origin.png)

If you change the repo name, you have to change the remote origin as well. To change the remote origin, use:
```
git remote set-url <url>
```

## Shortname to reference the Repo:

To add a new remote Git repository as a shortname you can reference easily, run ```git remote add <shortname> <url>```
![](images/reference%20the%20repo.png)

## Showing Your Remotes

To see which remote servers you have configured, you can run the ```git remote``` command. It lists the shortnames of each remote handle you’ve specified.

![](images/showing%20remotes.png)
--------------------------------------------------------------------------------------------
You can also specify ```-v```, which shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote:

![](images/showing%20remotes%202.png)


## Difference between Clone, Fetch and Pull


### git clone
The clone command in git is used when you want to download an existing git repository to your local computer.

### git pull
When you want to take changes or updates done by other developer/team member on git repository, you have to use git pull.
In detail git pull is the command that fetches the content from a remote repository and integrates it with the local repository/branch. It is, in actuality, a combination of git fetch and git merge called in that order.

### git fetch
Git "fetch" Downloads commits, objects and refs from another repository. It fetches branches and tags from one or more repositories.

---

## Listing Your Tags

Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (```v1.0```, ```v2.0``` and so on).
Listing the existing tags in Git is straightforward. Just type ```git tag``` (with optional ```-l``` or ```--list```)

## Creating Tags

Git supports two types of tags: lightweight and annotated.

### Lightweight Tags

A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.
```
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4-lw
```

### Annotated Tags

Annotated tags are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message. It’s generally recommended that you create annotated tags so you can have all this information.
```
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
Result:
v0.1
v1.3
```

## View Details of a tag

use:  ```git show <tag name>```

## Delete Tags

use: ```git tag -d <tag name>```
Note that this does not remove the tag from any remote servers.
The second (and more intuitive) way to delete a remote tag is with:
```git push origin --delete <tag name>```

---

## Creating a New Branch

What happens when you create a new branch? Well, doing so creates a new pointer for you to move around. Let’s say you want to create a new branch called ```newBranch```. You do this with the ```git branch``` command:
```
git branch newBranch
```
The ```git branch``` command only created a new branch — it didn’t switch to that branch.

## Switching Branches

To switch to an existing branch, you run the ```git checkout``` command. Let’s switch to the new ```newBranch``` branch:
```
git checkout newBranch
```
This moves ```HEAD``` to point to the ```newBranch``` branch.
--------------------------------------------------------------------------------------------
To create a new branch and switch to it at the same time, you can run the ```git checkout``` command with the ```-b``` switch:
```
git checkout -b iss53
Switched to a new branch "iss53"
```

## Merging

All you have to do is check out the branch you wish to merge into and then run the ```git merge``` command:
```
$ git checkout master
Switched to branch 'master'
$ git merge iss53
```

## Deleting

```
git branch -d iss53 OR 
git branch --delete <branchname>
```

### Questions
- Git commit creates a duplicate of a previous file with new changes in it. Does every git commit command takes up space in the local system?
Yes, every commit comand does save the files again in the local system. Though it saves only the changed parts of a file or files. So no data or file is being duplicated.
- Difference between git reset and git restore?
