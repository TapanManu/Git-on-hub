# git-commands

Git is an open source software for version control
popular git commands
Inspect different commits and branches
```
$ git checkout [SHA] 
```
resets HEAD to specfied SHA (HEAD is var that points to commit). In this way, 'travel' to different repo states.

```
$ git checkout HEAD~[number of commits to moveback] 
```

Alternate syntax. Don't have to log first, if you know how many commits you want to move back. $ git checkout master return to present repo state $ git checkout [branch] move to branch

RESET: revert back to prior state and destroy following commits.

 NOTE: Critical to understand that reset does not affect files, only commits!

Should only be done with code not being shared, i.e., local code that hasn't been pushed to remote repo. Use checkout to inspect previous commits, and reset to irreversibly revert back to.
Reset to SHA
```
$ git reset [SHA]
```

Reset by number of commits

```

$ git reset HEAD~[number of commits to move back]
```

Revert to older code history and also reset files to earlier state

```

$git reset --hard [SHA] or git reset --hard HEAD~[number of commits back]
```

Reset also used to discard uncommitted changes
Scenario: you're working locally, saving and running your app to test, 

and finally decide that you don't want to keep any of the changes you've made.

```
git reset --hard
```

# Branches

A branch is a parallel version of a repository. 

Example for when you'd want to make a branch is to develop a new feature. Changes made to branch have no effect on master,

and vice versa. Once the feature is ready for production, the local branch is merged into master and then pushed out to

production server.

Command quick-reference
```

git branch Display all branches. Asterisk (*) denotes active branch

git branch [branch-name] Create branch. Example: git branch feature/feature-name

git push -u origin [branch name] Create remote mirror of branch.

1.git branch -D features/featureA Delete a local branch and associated remote mirror

2. git push origin :features/featureA

git checkout [branch-name] Move to [branch-name]

git checkout -b [branch-name] Create and move to new branch in one step
```

# Creating branches

Scenario and workflow: you are tasked with creating a new feature for a web app.

First you would create a new branch, then switch to it with git checkout [new branch].

Two ways to create a branch:

Explicit with two steps
```
1.git branch [branch-name] Create branch

2.git checkout [branch-name]then move into it

One liner

git checkout -b [branch-name]Do both at once with checkout and -b flag
```

Create remote mirror and push new local branch one liner

`git push -u origin [branch name]`

note: the -u flag establishes a tracking connection between local and remote branches so that succeeding pushes may be done

with git push

# Merging branches

It's time to merge your branch back into master after you've tested your feature and all is good to go.

Before merging, it would be a good idea to run diff on the feature branch from master to verify that you're getting what

you'd expect.

Move into master from feature branch

`git checkout master`

Note: Could run git branch here to verify in master branch and practice basic commands

Run diff on feature branch to verify changes

```
git diff /features/feature-name

Run merge from master on feature branch`

git merge features/feature-name
```

Merging updates latest commit on master. Check this by running log. Hmm no info on merge.

```
git log
```

Merge with --no-ff to retain info about the merge. Log will display Merge info line. Recommend using this always

merge --no-ff features/feature

After merging, may wish to delete branch

```
git branch -d branch1

Delete remote branch

git push origin :branch1
```

Handling merge conflicts

Merge conflicts are a normal occurrence and happen when two branches have competing changes.

Conflicts in files are wrapped by <<<<<<< HEAD [one branch's code] ========== [other branch's version] >>>>>>>

 To resolve, simply edit code (You may want to keep code from different version,
 
 one or the other, or any variation thereof), remove <<<<<< HEAD ======== >>>>>>>, save file, and run git commit without -m
 
## Cloning repos and pushing local changes up to remote repo

## Creating remote repo
```
1. Click on new repo button after signing in to Github, name it, then click Create repository button

2a. Initialize local repo with git init in terminal, then copy and paste code from …or push an existing repository from the

command line on Github into terminal and run it. The -u flag allows following pushes from local master to be done with

truncated git push, rather than git push master.

2b. Could optionally first create remote repo on Github following steps above without first initializing local repo,

then copy and paste code from …or create a new repository on the command line on Github into terminal and run it.

It will accomplish the same thing.

Cloning repos

Click clone button in repo on Guthub, copy URL, nav to local dir, and run git clone URL.

No need to initialize local repo.
```

# Branches and Github

Suppose you have created a new branch locally to work on a feature and would like to push the branch up to Github. 

You cannot simply run git push in this instance, because only the master branch is being watched.

You must explicitly tell git to create a new remote branch on Github with 
```
git push -u origin [branch-name].
```

This code should be familiar as it's essentially the same that was used to make the initial push of local master repo to Github

## Merging upstream (remote) changes to local repo

Scenario: Your collaborators have made changes to the master branch, and you would like to update your local repo to incorporate those changes into your code.

1. Navigate to local directory containing repo and make sure you're in master branch with git branch

2. Run git fetch. This pulls down all the remote changes to local repo, but does not merge them.

3. Compare files with git status. Will say that your branch is behind

4. Run git merge

NOTE

May optionally run git pull which combines fetch and merge into one command

5. Resolve merge conflicts. This may require communicating with collaborators to grok their work.

# Pull requests and code review

 A pull request is a formal request to merge a set of changes from one branch of a repo into another.
 
 Imagine you've added a new feature to a collaborative project, you've tried it out locally, and you're confident it works. 
 
 After pushing to origin, you're ready to have that feature merged into the master branch of the project repository.
 
 It's time for a pull request, boy.
```

1. To initiate pull request, go to main repo page, and click on Pull requests tab,

then New pull request button, which displays an interface to compare branches.

base -- this is the branch that you want to merge your work into

compare -- the branch that contains your work

In Thinkful lesson, the pull request involved master as base> branch and features/add-index-html as compare branch.

In the mock scenario, we created a branch from master called feartures/add-inde-html created an index.html in it,

and now we want to merge it with the remote origin master

2. Click Create pull request button, and fill out form, including name and description for the request. 

Both name and d escription should be concise and understandable at a high level.

3. Click Create pull request button. The page will update, and a new Merge pull request button will appear.

At this point, you may add/review comments in files, by clicking on the Files changed tab to display them.

Pull request is LIVE at this point.

4. Any changes requested are carried out locally and pushed from local to origin where they will show up in PR.

```
