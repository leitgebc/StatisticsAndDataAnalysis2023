# Usage of Git

Usually, any piece of code or framework is developed and used by more than one person. Git provides a platform to co-develop code providing version control and special features like continuous integration, documentation and project management tools and is widely used in the scientific community as well as for industrial purposes. There are plenty of tutorials and documentations providing a very complete picture of the possibilities with git. The following is supposed to be an overview of the most common workflows for the statistics and data analysis tutorial as well as trouble shooting for the most likely problems. If you encounter any issue that is not mentioned here, please notify me via clara.leitgeb@physik.hu-berlin.de so I can follow up with you directly and if necessary make an addition to this document.

Even without a github account you are free to download shared code from a repository. However, if you would like to contribute to a project (i.e. change and upload material) or create your own repository, you will have to create a (free account) yourself. This can be done [here](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F%3Cuser-name%3E%2F%3Crepo-name%3E&source=header-repo&source_repo=aotownsend%2FStatMethods2022), providing an email address.

## The Git Repository

### Creating a new repository

### Protocols and keys

On GitHub you can find a large variety of repositories, with each's content serving different purposes. If you want to clone/pull/push... a repository, you can either do that via the https or the ssh protocol. The https protocol should work out of the box, although it might ask for your username and password. For ssh you have to add an ssh key in your account's profile. It will serve as an authentification when connecting to GitHub. Under your account's icon in the upper right corner, select the tab for ''settings''. In the left panel you can the select ''SSH and GPG keys''. On the right you will see a green button ''add new SSH key''. If you haven't got an ssh key yet, you will need to generate a new one on your local machine. For this follow the steps indicated in the corresponding [GitHub page](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). If you have generated your key, you need to copy the public key and add it into the text field on the aforementioned settings page.

### Cloning a repository

Both the https and the ssh URLs are given on each repository page in the upper right corner, clicking on the green button ''Code''. If you want to clone a repository (i.e. create a local copy of it) on your machine, you can simply copy either the https or the ssh URL and type into your terminal (at the location where you would like to store it):
```
git clone <https or ssh URL>
```
The repository will the be downloaded into that folder and the git environment will be created.

### Updating your local repository

You can pull the most latest version of the code, by simply typing:
```
git pull
```
However, if you have any local changes, you might create a conflict if there are changes in the same parts of the code in the remote version. In order not to mix up your own work, it can be prudent to first save your local changes in a stash:
```
git stash
```
Those changes are not applied anymore and the visible version is the one of your last pull. Then, you can download and apply the remote changes since your last update:
```
git fetch -a
git rebase origin main
```
Finally, you can apply your changes from before on top of the new version of the remote repository:
```
git stash apply
```
Don't forget to clean up the stash in order not to run into any problems next time:
```
git stash clear
```

### Pushing local changes

If you want to update the remote repository with your local changes, first make sure that your local repository is at the same version as the remote one by follwing the previously mentioned steps. Your changes will be collected in ''commits''. To stage a changed file for a commit, type:
```
git add <file name>
```
As soon as you have staged all new or changed files, you can create your commit by typing:
```
git commit -m <commit message>
```
It is very important to always include meaningful commit messages. In a project, in which many people contribute it might otherwise be very hard to track specific changes in the code. All commits appear in the ''history'' page of the remote repository.
So far, the commit is just registered locally. To upload it to the remote repository, type:
```
git push
```


### Navigating a repository

A developing repository can consist of all kinds of structures. There can be branches, tags and forks. 

#### Branches

Each repository usually has an ''origin/main'' branch that is the working baseling for all development. However, there can be plenty of different branches that can be used e.g. to develop new features while one doesn't want to have any interference from other changes that might go into the main branch in the mean time. From time to time, these branches can be merged with the main branch, to add the developed feature back into the main branch. To create a new branch locally you can simply type into your console:
```
git branch <new branch name>
```
The next time you push your changes to the remote repository, the new branch will be added there too. If you want to switch to an already existing branch locally, simply type:
```
git checkout <branch name>
```
All your changes will then be associated with that branch.
If a branch has served its purpose, it can also be deleted:
```
git branch -d <branch name>
```

#### Forks

Similarly to branches, forks can be used to develop a certain part of the code separately from main before merging it back. But it can also be used as a completely independent provate version of the code. To fork an existing repository, you can simply use the ''Fork'' button on the repository's main page. A new page for your forked repository will then be generated, which you can then clone locally as usual. This forked repository will the be your ''origin'' source. If you want to keep your fork updated concerning the changes in the original repository (e.g. because you want to merge your own changes back into it at some point), you need to let git know the original remote (''upstream'' source) address:

```
git remote add upstream <source>
```

Then you can pull updates from a branch (e.g. ''main'') of the upstream repository:
```
git pull upstream <branch name>
```
Finally you can push the changes to your forked remote repository (''origin''):
```
git push origin <branch name>
```

#### Tags

When developing code, it is useful to mark certain working versions (''release'') of it with a tag, so that it will be easily accessible later. These tags are frozen for further changes and can be accessed as:
```
git checkout <tag name>
```

## Useful commands

### Status

Whenever you are unsure on which branch you are currently working locally, which files have been changed and which of those have already been staged for commit, you can simply review all this information with
```
git status
```

### Commit history

If you want to see the history of your local commits, simply type
```
git log
```

### Differences in files

If you'd like to see if and which differences there are in a file in the remote repository with respect to the local version, you can use:
```
git diff <file name>
```

### List of branches

To see a list of all available branches, you can type:
```
git branch
```


### Merge conflicts

When updating the local repository with changes in remote, git is merging local and remote changes in individual files automatically. This works fine e.g. with white spaces but sometimes merge conflicts have to be resolved by the user.
In such cases I like to use the git mergetool, which will show you every merge conflict, the respective remote and local versions and lets you decide which version you want to keep. Simply type:
```
git mergetool
```
