title: Quick Tip - Speeding up "git status" in a repo with multiple submodules
date: 2013-07-26 02:49:25
tags:
- eclipse
- git
---
Something that's always bothered me was when I work on a repo that has numerous submodules, as more and more get added it seems like it takes longer and longer to run the command "git status".

It turns out this is due to git scanning all the directories to find untracked files so when it shows you the status in the aggregator repo it'll tell which repos have untracked files. For me I'd rather just find out which submodules have modifications and if there's any new commits most of the time.

It is possible to have git status ignore these untracked files and as a result speed up "git status" by adding the following line to your ".git/config" for each submodule you want to ignore untracked files for:

    ignore = dirty

Example:

    [submodule "submodule.repo"]
        url = ssh://localhost/submodule.repo
        ignore = dirty
