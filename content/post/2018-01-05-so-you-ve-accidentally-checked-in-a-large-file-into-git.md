---
title: So You've Accidentally Checked in a Large File Into Git
author: ~
date: '2018-01-05'
slug: so-you-ve-accidentally-checked-in-a-large-file-into-git
categories: [git, git hell]
tags: [git hell]
---

Greg Wilson first said it, but I've come to agree. Git is an aggressively antisocial piece of software. Git is a piece of software that can make developers with any amount of experience feel dumb. 

Recently, I accidently checked a large file (greater than 100M) into my local repo. When I tried to push to GitHub, of course, it refused it (I know about git large file storage, but I don't have any). 

So my local repo was screwed up. Of course, I did what seemed like the rational thing and deleted the file from my repo and recommitted. More than once. This is a mistake I've done 

BFG is supposed to make your life easier, but for some reason the directions always specify how to fix a *remote* repo. I would say that this situation is much less common than the local situation. I usually install it through `homebrew`, using `brew install bfg`.

Say you've accidently checked in a large file into your current repo. The first thing to do is to clone your local repo:

```
git clone --mirror local_repo
```

This will create another folder called `local_repo.git` that you will do all the BFG magic on. I want to remove any files larger than 100 Megs, so I do this:

```
bfg -b 100M local_repo.git
```

If this doesn't return an error, you can move on. However, I got the dreaded error:

```
Warning : no large blobs matching criteria found in packfiles - does the repo need to be packed?
```

Augh. Ok, some googling later I found that I needed to pack my orignal repo:

```
cd local_repo
git repack
```

Okay, we need to get rid of our cloned repo and redo the last few steps.

```
rm -rf local_repo.git
git clone --mirror local_repo
bfg -b 100M local_repo.git
```

Then comes some git commands that no one has bothered to explain to me.

```
git reflog expire --expire=now --all && git gc --prune=now --aggressive
git push
```

Uh oh, I get a `remote: error: refusing to update checked out branch: refs/heads/master` error! More ugh. 

Here's the trick. Since you clone a local repo, you need to set the origin of your current repo (`local_repo.git`) to the GitHub remote. First we remove the current `origin`, and then add back our remote.

```
git remote rm origin
git remote add origin https://github.com/laderast/remote_repo.git
```

Finally, after much gnashing of the teeth, we can

```
git pull
```

This may be obvious to the 10 people in the world who have read all of the git documentation, but I am not one of them. I'm stuck with git, unfortunately. I'm writing this post to remind me of what to do when I innocently do something like commit a large file to my repo.