---

layout: post
title:  "Draw Neat Trees With Git Rebase"
author: stephen
categories: [ Git, Rebase ]
tags: [red, yellow]
image: https://cdn-images-1.medium.com/max/9216/0*yAUsmcEoJaulRiRt
description: "Edit or discard your commits with interactive rebasing"

---

Rebasing a Git branch can be challenging. I’d recommend getting more familiar with it by reading “[Don’t Fret With Git Rebase](https://medium.com/better-programming/dont-fret-with-git-rebase-75fe3ed5ca8f)” before digging any further.

---

If you have decided to use this powerful command, you’ve already made the most significant step. You have flattened your Git history, creating a linear tree any person can read.

Is that all we can do? Of course not — we still haven’t harnessed the real power behind [Git rebase](https://git-scm.com/docs/git-rebase). I’ll show you how.

---

# Beyond Rebase

Let’s assume you have rebased and merged `neat_branch` and then `messy_branch` into `develop`:

![](https://cdn-images-1.medium.com/max/1656/1*AWrU-puqJt9C7Szx8OdZ6g.png)

The resulting tree appears flat and neat. Wouldn’t it be more helpful, though, to squeeze our tree even more? Maybe some commits could have been avoided?

While `neat_branch` seems fine, `messy_branch` contains several commits we could discard. Two commits present a “fix” prefix which may not bring much information. Even worse, someone pushed a temporary commit.

Git rebase provides an option to rewrite even further your Git history. Let’s clean up our mess.

---

# Interact With Your Rebase

When referring to the official [documentation](https://git-scm.com/docs/git-rebase#_interactive_mode), you can interact with your commits while rebasing your branch. Let’s focus on the following options:

- Pick (p): the default option. Basically, keep this commit as-is.

- Reword (r): Pick commit, but lets you rename the commit’s title.

- Squash (s): Merge commit’s content with the previous commit.

Word of caution: You can’t squash your first branch’s commit.

Back in our example, we’ll fuse several commits into one and rename the commit’s title to make it more relevant.

```
$ git fetch --all
$ git checkout messy_branch
$ git rebase -i origin/develop
```

Instantly we get prompted with our branch history.

```
pick 29d2bab First commit on messy branch
pick de7cdc8 Fix build
pick e120b7c Fix Unit tests
pick 8f79ef0 Tmp commit
pick ff1b89b Very bad tipo
pick c8c0ba5 Final commit
```

Now let’s squash a few irrelevant commits and rename one badly typed commit. We only interact with the commits we’re interested in.

```
pick 29d2bab First commit on messy branch
s de7cdc8 Fix build
s e120b7c Fix Unit tests
s 8f79ef0 Tmp commit
r ff1b89b Very bad tipo
pick c8c0ba5 Final commit
```

Let’s proceed with this setting. We will squash the second to fourth commits into the first one. We also take advantage to rename the fifth commit.

The rebase will stop when hitting the first squash. The prompter shows all your squashed commits about to become one, more significant commit. Validate and continue.

Finally comes the time to rename our poorly typed commit as requested above. Edit your commit’s name and pursue finalizing the rebase.

![](https://cdn-images-1.medium.com/max/1652/1*TRj2g9xuqlKhPxcmvimYwA.png)

Although it may look like a small improvement, I assure you it can save you from overstraining your eyes. Some branches could hold more than twenty commits each, compelling you to scroll down a lot before hitting what you’re looking for.

---

# Thoughts about squash?

People often ask me when we should squash. In my opinion, having separate commits for each task ease reviews and should be encouraged.

Once your teammates approve your pull request, you’re likely to rebase your branch onto the target branch before merging it. I recommend profiting from this operation by doing the last sweep.

I hope you’ll get into this habit of cleaning your Git history. This operation will benefit you as well as your entire team in the long run.

Keep in touch for more articles to come!
