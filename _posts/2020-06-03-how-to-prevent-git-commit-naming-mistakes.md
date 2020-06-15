---

layout: post
author: stephen
title: How to Prevent Git Commit Naming Mistakes
description: Throw a safety net each time you commit with Git hooks
categories: [ Git, Hooks ]
image: https://cdn-images-1.medium.com/max/12032/0*21xNCoRhStuuukMA

---

#### Throw a safety net each time you commit with Git hooks

I’ve been using Git for many years, and I’m still far from knowing it all. However, I feel like Git has the answer each time I face a problem. More recently, I’ve been wondering how we could remove the boredom of prefixing commit messages with a [Jira](https://www.atlassian.com/software/jira) ticket number.

I’ve always felt that naming my branches and commit messages was tedious. Despite this fact, I always strive to respect naming conventions. They’re vital to keeping proper versioning and helping your teammates seek your branches.

So what are the options? You can still manually name your branches, but it’s tedious and error-prone. If you use Git flow, you may be tempted by a [wrapper](https://danielkummer.github.io/git-flow-cheatsheet/index.fr_FR.html) to drive you through the naming. Unfortunately, my experience with it wasn’t conclusive. Besides, you may want some flexibility in your naming, and I found this tool too rigid.

Rejoice! Git always has an ace up its sleeve. You can intercept specific Git commands before they’re performed to execute scripts. They’re called [hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks).

I won’t describe them all. Instead, I’ll present two of them to:

1. Enforce a branch naming policy.

2. Prefix commit messages with the branch name ticket.

---

# 1. Enforcing Branch Naming Policy

I mentioned [Git flow](https://nvie.com/posts/a-successful-git-branching-model/) in my introduction. This branching convention is popular amongst developers. It results in prefixing your branches with names such as `master`, `develop`, `feature`, `bugfix`, and so on. When naming your branch, you may also want to append a ticket number.

At my company, we enforce this naming policy:

- Branches must start with one of the Git flow keywords followed by a splash.

- Then indicate the Jira project name and ticket number linked with a hyphen.

- Then the developer initials linked with an underscore.

- Finally, the description of the ticket.

One example would be:

```
feature/GTBC-9999_SV_git_hooks
```

A hook can check all those conditions. For instance, ensure that your branch name respects your policy before committing. You’ll need to add a `pre-commit` script file inside the `.git/hooks` folder.

Here is the script to enforce these conditions:

<script src="https://gist.github.com/StephenVinouze/20bb168ce7eb3966cd3e288eb41215e8.js" charset="utf-8"></script>

> For syntax purposes, this Gist is written with the `sh` file extension. Be sure to NOT use this extension or Git won’t read it.

Mark your file as executable:

```
$ chmod +x pre-commit
```

To better understand the Regex, have a look at the Regex representation. This illustration shows that it respects our branch naming policy.

![Photo made with [Regexper](https://regexper.com/).](https://cdn-images-1.medium.com/max/4008/1*OHi2YtxGmmjQMXv0bT4RYw.png)

If you try to commit from a branch that doesn't match your Regex pattern, you’ll get rejected before the commit is executed.

---

# 2. Prefixing Commit Messages

Naming conventions don’t only apply to branches. Each time you commit, you may be entitled to add extra information to your commit message. That could be your ticket number, for instance.

Git lets you edit your commit message automatically with a `prepare-commit-msg` hook. You get the original commit message as an argument, and you can manipulate it to your need.

Let’s revisit my example above. I’m developing a new feature to add Git hooks — how convenient — to my GTBC project. This task refers to the ticket number 9999, and my initials are SV.

One valid branch name would be:

```
feature/GTBC-9999_SV_git_hooks
```

And for this branch, I want all my commit messages to start with `[GTBC-9999]` followed by the actual developer message.

<script src="https://gist.github.com/StephenVinouze/03327d4b28b17b4eabe902dc3507dc2a.js" charset="utf-8"></script>

Here, `$1` refers to your original commit message. With the `grep` command, we extract the project name and ticket number from the branch name. Then we transform this extraction in uppercase. Finally, we print the final commit message before redirecting it into the Git commit message pipe.

Before testing your script, remember to mark your file as executable:

```
$ chmod +x prepare-commit-msg
```

With this hook plugged, here is the output:

![Git commit message was prefixed with [GTBC-9999]](https://cdn-images-1.medium.com/max/4376/1*as6-761YfAd2jrY9ZijYhQ.png)

Notice the `if` condition in the script. Sometimes, habits die hard. Some of your teammates may keep adding their ticket numbers manually.

To prevent redundancy, you can check whether the ticket number dwells inside the commit message — no need to add the ticket reference twice.

Let’s try this out:

![Purposefully adding [GTBC-9999] in so the commit message doesn’t get duplicated](https://cdn-images-1.medium.com/max/4192/1*JUcA9xs7623dr1QXPPvOkQ.png)

We caught the ticket number inside the commit message, skipping the process. We can check that our two commits were correctly named inside the logs:

![](https://cdn-images-1.medium.com/max/2460/1*9EfnUdxd-iSyGZk_-ynxeA.png)

With this hook, you no longer need to bother with prefixing your commit messages.

---

# Share Your Hooks With Your Teammates

I said above that you must put your hooks inside the `.git/hooks` folder. You should know that the `.git` folder is not under version control. Git will ignore each file under this folder.

If you keep them in this location, you won’t be able to:

- Share them with your team.

- Keep a history of your modifications on them.

Fortunately, you can change the default location where your hooks are executed. For instance, I’ve created a `.git-hooks` folder at the root of my project and put all my hooks into it.

At the root of your project, execute this command line to apply these changes:

```
$ git config core.hooksPath .git-hooks
```

Now version this folder, and your teammates will benefit from them.

---

# Go Global

What about my other projects? Do I have to add the hooks to all my projects sharing the same naming conventions?

With this strategy, yes.

Once again, Git has thought it through with [Template](https://git-scm.com/docs/git-init#_template_directory). You can create a template and avoid configuring your hooks all over again.

This article explains it in more detail:

> [**Create a global git commit hook (Example)**](https://coderwall.com/p/jp7d5q/create-a-global-git-commit-hook)

---

# Conclusion

I hope these two practical use cases will trigger your creativity. Automate the boring stuff and ensure that you don’t miss the mark when naming your commits!

Thank you for reading!
