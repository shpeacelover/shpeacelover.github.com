---
layout: post
title: "git常用命令"
date: 2013-07-23 18:55
comments: true
categories:Blog
---
以下是自己常用到的git命令:

git init
git add .
git commit -a -m 'comment'
git checkout .
git stauts
git remote add origin ssh://user@host/~/git/depot.git
git push origin master
git clone some-repository some-path
git clone --depth 50 some-repository
git add -u|--update
git add -A|--all
git commit -m "Some message" -a                 (****this will commit all modified files)

Unstage a modified file that’s been staged.
For example, to undo changes to cache.py, use this:
prompt> git reset HEAD -- cache.py

Undo all uncommitted changes to a file.
prompt> git checkout -- cache.py

git config credential.helper 'cache --timeout=3600'
(the above will cache our password)

git brach new
git checkout new
git checkout -b new

to view all local branches:
git branch
to iew all remote branches:
git branch -r
to view all branches:
git branch -a
to view all that are or are not merged into the current branch :
git branch --merged
git branch --no-merged

Merge changes from development to the master branch:
git checkout master
git merge development

Merge changes, but don’t commit:
git merge --no-commit development

Add a one-line log message from each merged commit to the merge message:
git merge --log development

















