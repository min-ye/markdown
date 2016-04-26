# GIT Training
## Setting
    git init
    git config --global user.name "Ye Min"
    git config --global user.email min_ye@outlook.com

## Local Repository
### Prepare files
##### Create files
Create three files: a.txt, b.txt, c.txt
a.txt: History Repository
b.txt: Staging Area
c.txt: Working Directory
    echo "Hello History Repository" > Repository.txt
    echo "Hello Staging Area" > Staging.txt
    echo "Hello Working Directory" > Working.txt

##### Put Repository.txt on History Repository
    git add Repository.txt
    git commit -m "commit repository"

##### Put Stage.txt on Staging Area
    git add Staging.txt

##### Search
    git grep "Repository"

##### Check log
    git log --stat
>--stat is used to see the file information

### Show difference
##### Change the file
    echo "Welcome Repository" >> Repository.txt
    echo "Welcome Staging" >> Staging.txt
    echo "Welcome Working" >> Working.txt
    git add Repository.txt

##### Show difference between Working Directory and Staging Area
    git diff





### Pull Conflict
If existing conflict when pull from remote, and the error message looks like

    error: Your local changes to 'c/environ.c' would be overwritten by merge.  Aborting.
    Please, commit your changes or stash them before you can merge.

It can be resolved by git stash

    git stash
> Save the current status, restore from History Repository

    git pull origin master
> Pull from remote

    git stash pop stash@{0}
> Restore the saved stash

Then merge it and commit.