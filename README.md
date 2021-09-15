# MyFirstGitHubProject

## Problem Statement

Five Developers are working in a startup. Their company wants a better Source Code Management System because the earlier tool had the tendency to save redundant code.
Multiple Developers working simultaneously on same block of code also caused problems. You and jake, and your manager has given you the task of moving company's codebase to git and Github

### Action Items
1. Create a local git repository and move the entire code base to it.
2. Create a new branch for a new feature you want to add to the application
3. Merge back the created branch with the master branch
4. Create a remote repository
5. Push the local repository to company's remote repository

Link to download the code base


## Solution:

### Pre-requisites

* Go to https://github.com/ and create an account
* Go to https://git-scm.com/downloads and install git

- Create a folder where you would want to work on.
- In my case i created a folder on my desktop named GitHub
- Open your terminal and type below command
    $ git version
- Output:
    git version 2.33.0.windows.2

### Action Item 1: Create a local git repository and move the entire code base to it.

You have to create a git local repository. First create a directory to separate it out.
    $ mkdir startupRepo

Change the current working dirctory
    $ cd startupRepo

    $ ls -alrt
    total 0
    drwxr-xr-x 1 gshem 197609 0 Sep 15 20:01 ../
    drwxr-xr-x 1 gshem 197609 0 Sep 15 20:01 ./


Initialize a git local project
    $ git init
Initialized empty Git repository in D:/Projects/GitHub/startupRepo/.git/

    $ ls -alrt
    total 4
    drwxr-xr-x 1 gshem 197609 0 Sep 15 20:01 ../
    drwxr-xr-x 1 gshem 197609 0 Sep 15 20:02 ./
    drwxr-xr-x 1 gshem 197609 0 Sep 15 20:02 .git/

you see there is a .git folder. So you have successfully initialized a git local repository

Now i need to put my company's codebase in this directory. Let me go ahead and copy my helloWorld.txt into this folder for demo purpose.

    $ ls -lart
    total 5
    drwxr-xr-x 1 gshem 197609  0 Sep 15 20:01 ../
    drwxr-xr-x 1 gshem 197609  0 Sep 15 20:02 .git/
    -rw-r--r-- 1 gshem 197609 36 Sep 15 20:06 helloWorld.txt
    drwxr-xr-x 1 gshem 197609  0 Sep 15 20:06 ./

    $ cat helloWorld.txt
    Hello..!!
    This is a startup project

Yeah..!! We have created a local git repository. Lets commit our code and see which branch are we in..

git status shows the status of your local git repository.
    $ git status
    starting fsmonitor-daemon in 'D:/Projects/GitHub/startupRepo'
    On branch master

    No commits yet

    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            helloWorld.txt

    nothing added to commit but untracked files present (use "git add" to track)


"git add" command adds the files which are untracted.

    $ git add .

"git commit" adds a comment to your changes and stages the code.

    $ git commit -m "My First commit"
    [master (root-commit) 590cd05] My First commit
    1 file changed, 2 insertions(+)
    create mode 100644 helloWorld.txt

After commit, you see that there is master branch and we dont have anymore untracked files.

    $ git status
    On branch master
    nothing to commit, working tree clean

"git branch" lists out the branches.

    $ git branch
    * master


### Action Item 2: Create a new branch for a new feature you want to add to the application

create a feature branch
    $ git branch feature/add-my-name

Now you can see your feature branch
    $ git branch
      feature/add-my-name
    * master

Switch to your feature branch
    $ git checkout feature/add-my-name
    Switched to branch 'feature/add-my-name'

Now you can see that you are on the feature branch
    $ git branch
    * feature/add-my-name
      master

You may check the status at any point of time.
    $ git status
    On branch feature/add-my-name
    nothing to commit, working tree clean

You have the same files as in your master branch. You can change the content in your feature branch without touching master branch.
    $ cat helloWorld.txt
    Hello..!!
    This is a startup project

Added below line in the file.
    $ cat helloWorld.txt
    Hello..!!
    This is a startup project
    I am hemanththedevopsengineer..!!

Now you need to add the file.
    $ git add .

commit the changes so that it is saved and tracked. do not switch branch with untracked work.
    $ git commit -m "adding my name"
    [feature/add-my-name 1d4ba81] adding my name
    1 file changed, 1 insertion(+)

Now you can see that your branch is clean.
    $ git status
    On branch feature/add-my-name
    nothing to commit, working tree clean

Switch back t master branch and see if the content was changed in master branch as well
    $ git checkout master
    Switched to branch 'master'

Answer is No. Now you see that you have 2 different versions of code which you can work on.
    $ cat helloWorld.txt
    Hello..!!
    This is a startup project

### Action Item 3: Merge back the created branch with the master branch

Once you are ready with your feature branch code, merge it to master branch. Before that make sure you are on the master branch.
If not do a git checkout master.
    $ git checkout master
    Switched to branch 'master'

Next merge the branch as below.
    $ git merge feature/add-my-name
    Updating 590cd05..1d4ba81
    Fast-forward
    helloWorld.txt | 1 +
    1 file changed, 1 insertion(+)

Now you can verify that the code you commited in your feature branch is merged to master
    $ cat helloWorld.txt
    Hello..!!
    This is a startup project
    I am hemanththedevopsengineer..!!

### Action Item 4: Create a remote repository

Now go to guthub where you had registered as per pre-requisites and create a repository with name startupRepo.
If you are facing difficulty. follow through on https://docs.github.com/en/get-started/quickstart/create-a-repo

### Action Item 5: Push the local repository to company's remote repository

Get the repository link and add your username@github.com as shown below.
    $ git remote add origin https://hemanththedevopsengineer@github.com/HemanthDevopsLearnings/startupRepo.git

Execute below command.
    $ git push origin master
    info: please complete authentication in your browser...
    Enumerating objects: 6, done.
    Counting objects: 100% (6/6), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (6/6), 540 bytes | 540.00 KiB/s, done.
    Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
    remote:
    remote: Create a pull request for 'master' on GitHub by visiting:
    remote:      https://github.com/HemanthDevopsLearnings/startupRepo/pull/new/master
    remote:
    To https://github.com/HemanthDevopsLearnings/startupRepo.git
    * [new branch]      master -> master


Check your repository and you would see helloWord.txt file in master branch.

Any queries. Feel free to reach out on my slack channel
https://hemanththedev-wqt5693.slack.com/archives/C02EF5LUATX
