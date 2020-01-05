---
title: 如何重新命名Git分支（how to rename a git branch locally and remotely?
date: 2017-12-15 22:33:15
tags: Git
---


1. git branch -m <old_name> <new_name>
2. git checkout <new_name>
3. git push origin <new_name>
4. git push origin -d <old_name>

参考自：https://stackoverflow.com/questions/36999937/how-to-rename-a-git-branch-locally-and-remotely++
